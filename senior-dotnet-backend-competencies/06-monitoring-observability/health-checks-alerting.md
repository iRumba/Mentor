# Health checks, алертинг

## Health Checks в ASP.NET Core
- `AddHealthChecks()` + `MapHealthChecks("/health")` — встроенный механизм.
- **Liveness** — сервер жив? (базовый: процесс работает).
- **Readiness** — готов принимать трафик? (БД, кэш, внешние сервисы).

## Кастомные проверки
- `IHealthCheck` — интерфейс с методом `CheckHealthAsync()`.
- `HealthCheckResult.Healthy()` / `.Degraded()` / `.Unhealthy()`.
- Пример: проверка соединения с БД, ответа от downstream API.
- Tagging — группировка (`ready`, `live`, `db`).

## Публикация метрик
- `AddHealthChecks().AddDbContextCheck<T>()` — встроенная проверка EF Core.
- `AspNetCore.Diagnostics.HealthChecks` — богатая библиотека проверок (БД, Redis, Kafka, RabbitMQ).
- `/health` → 200 (Healthy) / 503 (Unhealthy).

## Алертинг
- **Integration с Kubernetes**: livenessProbe, readinessProbe → Pod restart (Liveness).
- **Grafana Alerts** — пороговые уведомления.
- **Azure Monitor / Application Insights** — alert rules.
- **PagerDuty, OpsGenie, Slack** — каналы оповещений.

## Важно для интервью
- Разница Liveness vs Readiness: Liveness → restart, Readiness → трафик.
- Degraded — что-то не идеально, но сервис работает (полу-здоров).
- Graceful degradation — отключать часть функциональности, не весь сервис.
