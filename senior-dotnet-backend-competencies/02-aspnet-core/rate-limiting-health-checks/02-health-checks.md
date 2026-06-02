## Health Checks
- Мониторинг состояния сервиса: `/health`, `/health/ready`, `/health/live`.
- `AddHealthChecks()` + проверки БД, кэша, внешних сервисов.
- **Liveness** — сервер жив? (базовый).
- **Readiness** — готов принимать трафик? (БД, кэш).
- Публикация через `MapHealthChecks()`, интеграция с Kubernetes probes.
