# Middleware Customisation

Middleware (промежуточное ПО) — это компоненты, которые собираются в конвейер (pipeline) для обработки входящих HTTP-запросов и формирования исходящих ответов.

## Основы конвейера

Каждый middleware в цепочке имеет доступ к `HttpContext` и ссылке на следующий middleware в конвейере (`RequestDelegate next`).

**Порядок регистрации имеет критическое значение.** Запрос проходит через все middleware сверху вниз, а ответ возвращается в обратном порядке (снизу вверх).

## Способы добавления middleware

### 1. Инлайновый (Use)
Простой способ добавить логику прямо в `Program.cs`.
```csharp
app.Use(async (context, next) => {
    // Логика ДО следующего middleware
    var start = DateTime.UtcNow;
    
    await next(); // Переход к следующему
    
    // Логика ПОСЛЕ (когда ответ возвращается назад)
    var duration = DateTime.UtcNow - start;
});
```

### 2. Классовый подход (Custom Middleware)
Для сложной логики создается отдельный класс.

```csharp
public class RequestLoggingMiddleware {
    private readonly RequestDelegate _next;

    public RequestLoggingMiddleware(RequestDelegate next) {
        _next = next;
    }

    public async Task InvokeAsync(HttpContext context) {
        // Логика здесь
        await _next(context);
    }
}

// Регистрация через Extension метод
public static class MiddlewareExtensions {
    public static IApplicationBuilder UseRequestLogging(this IApplicationBuilder app) {
        return app.UseMiddleware<RequestLoggingMiddleware>();
    }
}
```

## Продвинутые инструменты ветвления

### Map
Позволяет создать отдельную ветку конвейера для конкретного пути.
```csharp
app.Map("/admin", adminApp => {
    adminApp.Use(async (context, next) => {
        // Специфичная логика только для /admin
        await next();
    });
    adminApp.Run(async context => {
        await context.Response.WriteAsync("Admin Panel");
    });
});
```

### When / UseWhen
Позволяет выполнять middleware только при соблюдении определенного условия.
```csharp
app.UseWhen(context => context.Request.Path.StartsWithSegments("/api"), appBuilder => {
    appBuilder.UseMiddleware<ApiSpecificMiddleware>();
});
```

### Run (Терминальный Middleware)
`Run` создает middleware, который **не вызывает next**. Это конечная точка конвейера. Все, что написано после `app.Run()`, никогда не будет выполнено.

## Сравнение: Middleware vs Filters

Многие путают Middleware и Action Filters. В чем разница?

| Характеристика | Middleware | Action Filters |
| :--- | :--- | :--- |
| **Уровень доступа** | Весь HTTP-запрос (HttpContext) | Уровень MVC/API (ActionContext) |
| **Область применения** | Глобально для всех запросов | Только для конкретных контроллеров/методов |
| **Доступ к метаданным** | Ограничен (только через Request) | Полный (доступ к параметрам метода, атрибутам) |
| **Порядок вызова** | Раньше всех (очень рано) | Позже (после маршрутизации) |

**Когда использовать:**
- **Middleware:** Логирование, Аутентификация, CORS, Сжатие (Gzip), Обработка исключений.
- **Filters:** Валидация параметров, Кэширование ответов метода, Логика, специфичная для бизнеса API.
