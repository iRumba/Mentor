## OAuth 2.0
- **Протокол авторизации** — делегирование доступа (не аутентификация!).
- **Роли**: Resource Owner (User), Client (App), Authorization Server, Resource Server.
- **Grant Types** (Flow):
  - *Authorization Code* — самый безопасный для Web Apps (с PKCE для SPA).
  - *Client Credentials* — server-to-server (без пользователя).
  - *Implicit* (устарел) — deprecated с OAuth 2.1.
  - *Resource Owner Password* (устарел) — только в легаси.
