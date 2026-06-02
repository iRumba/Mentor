# SQL Injection, XSS, CSRF

## SQL Injection
- Внедрение SQL-кода через пользовательский ввод.
- Пример: `' OR 1=1; --` — обход аутентификации.
- **Защита**: параметризованные запросы (`SqlCommand.Parameters`, Dapper, EF Core).
- **Никогда**: конкатенация SQL-строк с пользовательскими данными.
- EF Core и Dapper по умолчанию защищают (но `FromSqlRaw` — с осторожностью).

## XSS (Cross-Site Scripting)
- Внедрение JavaScript-кода на страницу через пользовательский ввод.
- **Stored XSS** — скрипт сохраняется в БД и выполняется при загрузке страницы.
- **Reflected XSS** — скрипт в URL/параметрах запроса.
- **DOM-based XSS** — клиентский скрипт вставляет недоверенные данные в DOM.
- **Защита**: эскейпинг вывода (HTML Encode), CSP (Content Security Policy), `@` в Razor автоматически эскейпит.

## CSRF (Cross-Site Request Forgery)
- Атакующий заставляет пользователя выполнить нежелательное действие на сайте, где он аутентифицирован.
- Пример: скрытая форма на стороннем сайте → POST на /api/transfer.
- **Защита**: Anti-forgery tokens (`[ValidateAntiForgeryToken]` в ASP.NET Core).
- SameSite Cookie (`SameSite=Strict/Lax`), CORS, Origin/Referer проверка.

## Важно для интервью
- SQL injection — самая базовая, но и самая критичная уязвимость.
- Input validation vs Output encoding — разная цель.
- Razor Pages автоматически защищают от XSS (эскейп по умолчанию).
- CSRF актуальна только при cookie-based auth (не JWT в header).
