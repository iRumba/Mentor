# Secure Coding Practices

## Принципы
- **Defense in depth** — несколько уровней защиты (не полагаться на одну).
- **Least privilege** — минимально необходимые права.
- **Secure by default** — безопасные настройки по умолчанию.
- **Fail securely** — при ошибке не раскрывать детали (500 без stack trace).

## Практики для .NET
- **Data Protection API** (`IDataProtector`) — шифрование чувствительных данных.
- `Cryptography.RandomNumberGenerator` — криптостойкая генерация случайных чисел (не `Random`).
- **ASP.NET Core** автоматически защищает от CSRF, XSS (Razor), переполнения запроса.
- **HTTPS** — `AddHttpsRedirection()`, HSTS (`Strict-Transport-Security`).

## Избегать
- Хранение паролей в открытом виде → использовать `PasswordHasher<TUser>` (bcrypt/PBKDF2/Argon2).
- Свои криптоалгоритмы — использовать ASP.NET Core Identity, библиотеки.
- Раскрытие stack trace в Production.
- Небезопасная десериализация (`BinaryFormatter`, `JavaScriptSerializer` — deprecated).
- Устаревшие библиотеки — регулярно обновлять (Dependabot, `dotnet list package --vulnerable`).

## SAST / DAST
- **SAST** (Static Analysis) — SonarQube, Roslyn analyzers, `dotnet format --verify-no-changes`.
- **DAST** (Dynamic Analysis) — OWASP ZAP, Burp Suite.
- **SCA** (Software Composition Analysis) — Dependabot, Snyk, NuGet Audit.

## Важно для интервью
- Shift left — безопасность на ранних этапах разработки.
- Microsoft Security Development Lifecycle (SDL).
- Регулярные code review с фокусом на безопасность.
