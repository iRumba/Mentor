## Authentication (аутентификация)
- Определяет кто пользователь. Реализуется через `AuthenticationHandler`.
- `AddAuthentication().AddJwtBearer()` / `AddCookie()` / `AddOAuth()`.
- Результат — `ClaimsPrincipal` в `HttpContext.User`.
