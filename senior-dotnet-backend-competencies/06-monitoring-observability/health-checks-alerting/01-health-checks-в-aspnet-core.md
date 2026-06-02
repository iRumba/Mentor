## Health Checks в ASP.NET Core
- `AddHealthChecks()` + `MapHealthChecks("/health")` — встроенный механизм.
- **Liveness** — сервер жив? (базовый: процесс работает).
- **Readiness** — готов принимать трафик? (БД, кэш, внешние сервисы).
