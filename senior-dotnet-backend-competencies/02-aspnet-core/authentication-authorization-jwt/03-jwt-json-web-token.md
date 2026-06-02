## JWT (JSON Web Token)
- Формат: `header.payload.signature` (Base64Url).
- Stateless — сервер не хранит сессию, вся информация в токене.
- `AddJwtBearer()` — валидация подписи, issuer, audience, lifetime.
- Access token (короткий) + Refresh token (длинный) — стандартный подход.
