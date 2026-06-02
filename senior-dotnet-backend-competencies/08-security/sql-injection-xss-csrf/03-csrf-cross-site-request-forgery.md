## CSRF (Cross-Site Request Forgery)
- Атакующий заставляет пользователя выполнить нежелательное действие на сайте, где он аутентифицирован.
- Пример: скрытая форма на стороннем сайте → POST на /api/transfer.
- **Защита**: Anti-forgery tokens (`[ValidateAntiForgeryToken]` в ASP.NET Core).
- SameSite Cookie (`SameSite=Strict/Lax`), CORS, Origin/Referer проверка.
