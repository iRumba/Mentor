# Options Pattern

Options Pattern — это способ использования классов для предоставления строго типизированных параметров конфигурации. Это позволяет разделить настройки приложения на логические блоки и избежать зависимости всего приложения от тяжелого интерфейса `IConfiguration`.

## Интерфейсы IOptions

В зависимости от того, как настройки должны обновляться в процессе работы приложения, используются разные интерфейсы.

### 1. IOptions\<T\> (Singleton)
Самый простой интерфейс. Регистрируется как Singleton. Значения читаются один раз при первом обращении и больше не обновляются до перезапуска приложения.
- **Когда использовать:** Для настроек, которые гарантированно не изменятся без перезагрузки (например, название приложения).
- **Особенность:** Не поддерживает Hot Reload.

```csharp
public class MyService(IOptions<MySettings> options) {
    private readonly MySettings _settings = options.Value;
}
```

### 2. IOptionsSnapshot\<T\> (Scoped)
Регистрируется как Scoped. Значения перечитываются из конфигурации при каждом новом запросе (HTTP-запросе). 
- **Когда использовать:** Для настроек, которые могут меняться «на лету», и вы хотите, чтобы в рамках одного запроса значения были консистентны.
- **Особенность:** Обновляется при изменении файла конфигурации, но только при создании нового Scope.

```csharp
public class MyService(IOptionsSnapshot<MySettings> options) {
    // options.Value будет актуальным на момент начала текущего запроса
}
```

### 3. IOptionsMonitor\<T\> (Singleton)
Регистрируется как Singleton, но предоставляет доступ к актуальным значениям в любой момент времени.
- **Когда использовать:** В Singleton-сервисах, где нужен доступ к обновленным настройкам без перезапуска.
- **Особенность:** Имеет метод `OnChange()`, который позволяет подписаться на событие изменения конфигурации.

```csharp
public class MyService(IOptionsMonitor<MySettings> monitor) {
    public void Process() {
        var currentLimit = monitor.CurrentValue; // Всегда актуально
    }
}
```

## Сводная таблица различий

| Интерфейс | Время жизни | Обновление | Применение |
| :--- | :--- | :--- | :--- |
| `IOptions<T>` | Singleton | Только при рестарте | Статические настройки |
| `IOptionsSnapshot<T>` | Scoped | При каждом запросе | Динамические настройки в HTTP-запросе |
| `IOptionsMonitor<T>` | Singleton | Мгновенно | Singleton-сервисы, real-time изменения |

## Регистрация и внедрение

```csharp
// В Program.cs
builder.Services.Configure<MySettings>(builder.Configuration.GetSection("MySettings"));

// В сервисе
public class ProcessingService(IOptionsSnapshot<MySettings> options) { ... }
```

## Best Practices

- **Избегайте IConfiguration в сервисах:** Вместо того чтобы внедрять `IConfiguration` и вызывать `config["Section:Key"]`, внедряйте конкретный `IOptions<T>`. Это делает сервис тестируемым (мокается POCO класс).
- **Валидация:** Используйте DataAnnotations в классах настроек для автоматической проверки корректности данных.
