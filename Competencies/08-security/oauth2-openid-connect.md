# OAuth 2.0 / OpenID Connect

## OAuth 2.0
- **Протокол авторизации** — делегирование доступа (не аутентификация!).
- **Роли**: Resource Owner (User), Client (App), Authorization Server, Resource Server.
- **Grant Types** (Flow):
  - *Authorization Code* — самый безопасный для Web Apps (с PKCE для SPA).
  - *Client Credentials* — server-to-server (без пользователя).
  - *Implicit* (устарел) — deprecated с OAuth 2.1.
  - *Resource Owner Password* (устарел) — только в легаси.

## OpenID Connect (OIDC)
- **Надстройка над OAuth 2.0** — добавляет аутентификацию (кто пользователь).
- Возвращает **ID Token** (JWT) — информация о пользователе.
- **UserInfo endpoint** — детальная информация о пользователе.
- **Discovery** — `/.well-known/openid-configuration` — метаданные (endpoints, JWKS).

## JWT в OIDC
- Access Token — доступ к API (JWT или opaque).
- ID Token — информация об аутентификации (всегда JWT).
- `sub` — уникальный идентификатор пользователя.
- `iss` — кто выпустил токен, `aud` — для кого.

## Реализация в .NET
- `Microsoft.Identity.Web` — интеграция с Azure AD.
- `Duende IdentityServer` / `OpenIddict` — если нужен свой IdP.
- `AddAuthentication().AddOpenIdConnect()` — OIDC handler.

## Важно для интервью
- OAuth 2.0 — про delegation (что разрешено). OIDC — про identity (кто).
- PKCE (Proof Key for Code Exchange) — защита Authorization Code flow для SPA.
- Token lifetime: access token (короткий), refresh token (длинный, можно отозвать).
