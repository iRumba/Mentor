# Middleware pipeline, lifecycle запроса

## Middleware pipeline
- Конвейер из компонентов (middleware), через который проходит каждый HTTP-запрос.
- Каждый middleware может обработать запрос, передать его дальше (`next`) или прервать цепочку.
- Порядок регистрации в `Program.cs` важен — это порядок выполнения.

## Жизненный цикл запроса
1. HTTP-запрос → Kestrel / IIS → ASP.NET Core pipeline.
2. Middleware выполняются в порядке регистрации (вход), затем в обратном (выход).
3. После pipeline — endpoint (контроллер / minimal API).
4. Ответ проходит pipeline в обратном порядке.

## Типы middleware
- **Conventional middleware** — класс с методом `InvokeAsync(HttpContext, RequestDelegate)`.
- **Inline middleware** — `app.Use(async (ctx, next) => ...)`.
- **Short-circuit** — `app.Run(ctx => ...)` — терминальный middleware.

## Важно для интервью
- `app.Use()` vs `app.Map()` vs `app.Run()`.
- Как работает `RequestDelegate` — связный список функций.
- Middleware для CORS, аутентификации, статических файлов — встроенные примеры.
- Порядок: ExceptionHandler → HSTS → HTTPS → StaticFiles → Routing → Auth → Endpoint.
