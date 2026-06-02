# Authentication / Authorization

## Authentication (аутентификация)
- Определяет кто пользователь. Реализуется через `AuthenticationHandler`.
- `AddAuthentication().AddJwtBearer()` / `AddCookie()` / `AddOAuth()`.
- Результат — `ClaimsPrincipal` в `HttpContext.User`.

## Authorization (авторизация)
- Определяет что пользователю разрешено. `[Authorize]`, `[AllowAnonymous]`.
- **Policies** — `AddAuthorization(options => options.AddPolicy("AdminOnly", policy => policy.RequireRole("Admin")))`.
- **Claims-based** — проверка наличия claim с определённым значением.
- **Roles-based** — проверка роли пользователя (через `IsInRole`).

## JWT (JSON Web Token)
- Формат: `header.payload.signature` (Base64Url).
- Stateless — сервер не хранит сессию, вся информация в токене.
- `AddJwtBearer()` — валидация подписи, issuer, audience, lifetime.
- Access token (короткий) + Refresh token (длинный) — стандартный подход.

## Важно для интервью
- Разница между Authentication и Authorization.
- JWT vs Session/Cookie — когда что выбирать.
- Проверка JWT без обращения к БД — в чём компромисс (невозможно отозвать).
- Refresh token rotation и reuse detection.
