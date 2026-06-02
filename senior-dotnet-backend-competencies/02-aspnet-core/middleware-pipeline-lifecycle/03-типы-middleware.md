## Типы middleware
- **Conventional middleware** — класс с методом `InvokeAsync(HttpContext, RequestDelegate)`.
- **Inline middleware** — `app.Use(async (ctx, next) => ...)`.
- **Short-circuit** — `app.Run(ctx => ...)` — терминальный middleware.
