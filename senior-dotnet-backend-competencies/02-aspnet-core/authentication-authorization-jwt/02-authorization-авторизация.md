## Authorization (авторизация)
- Определяет что пользователю разрешено. `[Authorize]`, `[AllowAnonymous]`.
- **Policies** — `AddAuthorization(options => options.AddPolicy("AdminOnly", policy => policy.RequireRole("Admin")))`.
- **Claims-based** — проверка наличия claim с определённым значением.
- **Roles-based** — проверка роли пользователя (через `IsInRole`).
