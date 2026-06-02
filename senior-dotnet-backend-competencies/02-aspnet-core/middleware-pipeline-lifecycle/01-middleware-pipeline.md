## Middleware pipeline

Middleware — это программные компоненты, которые собираются в конвейер (pipeline) для обработки HTTP-запросов и ответов.

### Технические детали и внутреннее устройство
Конвейер работает по принципу **Chain of Responsibility**. Каждый компонент middleware принимает `HttpContext` и делегат `RequestDelegate` (ссылку на следующий компонент в цепочке).

Когда запрос входит в систему, он проходит через каждый middleware по порядку их регистрации. Каждый компонент может:
1. Выполнить логику **до** передачи запроса следующему компоненту.
2. Вызвать `await next(context)`, передавая управление дальше.
3. Выполнить логику **после** того, как управление вернулось из следующего компонента.
4. **Прервать цепочку (short-circuiting)**, не вызывая `next`, и вернуть ответ сразу (например, если запрос не прошел авторизацию).

### Best Practices и типичные ошибки
- **Порядок регистрации имеет решающее значение**: Если вы поставите `UseStaticFiles()` после `UseAuthorization()`, статические файлы будут доступны только авторизованным пользователям.
- **Избегайте тяжелых операций в каждом запросе**: Middleware выполняется для каждого HTTP-вызова. Перенесите тяжелую инициализацию в конструктор или используйте кэширование.
- **Осторожность с Dependency Injection**: middleware являются синглтонами по умолчанию (если они зарегистрированы через `UseMiddleware<T>`). Не внедряйте Scoped-сервисы в конструктор middleware; используйте `InvokeAsync(HttpContext context, IMyScopedService service)`.

### Пример реализации
```csharp
public class CustomLoggingMiddleware
{
    private readonly RequestDelegate _next;
    private readonly ILogger<CustomLoggingMiddleware> _logger;

    public CustomLoggingMiddleware(RequestDelegate next, ILogger<CustomLoggingMiddleware> logger)
    {
        _next = next;
        _logger = logger;
    }

    public async Task InvokeAsync(HttpContext context)
    {
        _logger.LogInformation("Запрос: {Method} {Path}", context.Request.Method, context.Request.Path);
        
        // Эта часть выполняется ПЕРЕД следующим middleware
        await _next(context); 
        
        // Эта часть выполняется ПОСЛЕ возврата из всей цепочки ниже
        _logger.LogInformation("Ответ: {StatusCode}", context.Response.StatusCode);
    }
}

// Регистрация в Program.cs
app.UseMiddleware<CustomLoggingMiddleware>();
```

### Сравнение с альтернативами
- **Фильтры (Filters)**: Работают только внутри MVC/API контекста. Middleware работают на уровне всего HTTP-запроса, даже до того, как будет определен Endpoint.
- **DelegatingHandlers**: Используются в `HttpClient` для перехвата исходящих запросов. Middleware перехватывают входящие.
