## Типы middleware

В ASP.NET Core существует несколько способов определения и регистрации middleware, каждый из которых подходит для разных сценариев.

### 1. Conventional Middleware (Классический подход)
Это полноценный класс, который следует определенному соглашению.
- **Особенности**: Имеет конструктор, принимающий `RequestDelegate`, и метод `InvokeAsync`.
- **Преимущества**: Лучшая переиспользуемость, возможность полноценного DI в конструкторе.

```csharp
public class MyMiddleware
{
    private readonly RequestDelegate _next;
    public MyMiddleware(RequestDelegate next) => _next = next;

    public async Task InvokeAsync(HttpContext context, IMyService service) 
    {
        // service внедряется прямо в метод InvokeAsync (Scoped)
        await _next(context);
    }
}
```

### 2. Inline Middleware (Лямбда-выражения)
Быстрый способ добавить логику прямо в `Program.cs` с помощью `app.Use()`.
- **Особенности**: Позволяет описывать логику на месте.
- **Применение**: Простые проверки, логирование для отладки, маленькие хелперы.

```csharp
app.Use(async (context, next) => 
{
    // Логика ДО
    await next();
    // Логика ПОСЛЕ
});
```

### 3. Terminal Middleware (Терминальные компоненты)
Компоненты, которые не вызывают `next()`, тем самым завершая конвейер.
- **Метод**: `app.Run()`.
- **Применение**: Конечные точки, страницы "404 Not Found", Health Checks (в простых случаях).

```csharp
app.Run(async context => 
{
    await context.Response.WriteAsync("Hello from terminal middleware!");
});
```

### 4. Расширения (Extension Methods)
Хотя это не "тип" middleware, это стандарт оформления. Все сложные middleware оборачиваются в метод расширения для `IApplicationBuilder`.

```csharp
public static class MyMiddlewareExtensions 
{
    public static IApplicationBuilder UseMyCustomMiddleware(this IApplicationBuilder app) 
        => app.UseMiddleware<MyMiddleware>();
}
// В Program.cs: app.UseMyCustomMiddleware();
```

### Сравнительная таблица

| Тип | DI в конструкторе | DI в Invoke | Прерывает цепочку | Когда использовать |
| :--- | :---: | :---: | :---: | :--- |
| **Conventional** | Да (Singleton) | Да (Scoped) | Опционально | Переиспользуемый код, сложная логика |
| **Inline** | Нет | Нет | Опционально | Простые задачи, быстрые пробы |
| **Terminal** | Нет | Нет | **Всегда** | Конечные эндпоинты, заглушки |

### Common Pitfalls
- **Забытый `await next()`**: Если вы используете `app.Use()` и забываете вызвать `next()`, запрос просто "зависнет" или вернет пустой ответ, а последующие middleware (включая контроллеры) не выполнятся.
- **Неправильный DI в Conventional**: Попытка внедрить `DbContext` в конструктор `MyMiddleware` приведет к ошибке, так как middleware живет всё время работы приложения, а `DbContext` — только один запрос. Нужно внедрять в `InvokeAsync`.
