## Scope (Область видимости)

`IServiceScope` позволяет создавать изолированные области видимости для разрешения зависимостей. Это критически важно в сценариях, где стандартный жизненный цикл HTTP-запроса отсутствует или должен быть имитирован.

### Для чего нужен Scope?

По умолчанию в ASP.NET Core для каждого HTTP-запроса создается свой Scope. Все сервисы, зарегистрированные как `Scoped`, живут в пределах этого запроса. Однако в некоторых случаях нам нужно создать такой контекст вручную.

### Использование в фоновых задачах (IHostedService / BackgroundService)

`BackgroundService` является Singleton-сервисом. Если в его конструкторе попытаться внедрить `Scoped` сервис (например, `DbContext`), возникнет ошибка `InvalidOperationException` (Scope Validation), так как Singleton не может зависеть от Scoped-сервиса.

**Правильный подход**: внедрение `IServiceScopeFactory`.

```csharp
public class MyBackgroundWorker : BackgroundService
{
    private readonly IServiceScopeFactory _scopeFactory;

    public MyBackgroundWorker(IServiceScopeFactory scopeFactory)
    {
        _scopeFactory = scopeFactory;
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        while (!stoppingToken.IsCancellationRequested)
        {
            using (IServiceScope scope = _scopeFactory.CreateScope())
            {
                var dbContext = scope.ServiceProvider.GetRequiredService<MyDbContext>();
                // Работа с БД в изолированном scope
            }
            await Task.Delay(10000, stoppingToken);
        }
    }
}
```

### Внутреннее устройство

Когда вызывается `CreateScope()`, контейнер создает новый экземпляр `IServiceProvider` (дочерний), который:
1. Хранит свои собственные экземпляры `Scoped` сервисов.
2. Для `Singleton` сервисов обращается к родительскому (корневому) контейнеру.
3. Гарантирует, что при вызове `scope.Dispose()` все созданные в нем `IDisposable` объекты будут корректно очищены.

### Общие ошибки
- **Забытый Dispose**: Если создавать scope вручную и не обертывать его в `using`, возникнет утечка памяти (сервисы не будут уничтожены до завершения приложения).
- **Слишком длинный Scope**: Создание одного Scope на всё время работы фонового процесса приведет к разрастанию `DbContext` (он будет кэшировать все объекты в ChangeTracker), что вызовет деградацию производительности. Scope должен быть максимально коротким.