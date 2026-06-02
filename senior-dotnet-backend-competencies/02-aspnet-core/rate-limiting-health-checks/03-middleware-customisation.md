## Middleware customisation
- `IApplicationBuilder` — кастомная логика через `Use`, `Map`, `When`.
- `Run` — терминальный middleware (не вызывает next).
- `Map` — ветвление по пути (`/admin` → своя цепочка).
- `UseWhen` — условное выполнение middleware.
