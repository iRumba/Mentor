# Rate limiting, Health checks, Middleware customisation

## Rate Limiting
- Ограничение количества запросов от клиента за интервал времени.
- .NET 7+ — встроенный `AddRateLimiter()`.
- Алгоритмы:
  - **Fixed window** — фиксированное окно (напр. 100 запросов в минуту).
  - **Sliding window** — скользящее окно, сегментированный счётчик.
  - **Token bucket** — накопление токенов с постоянной скоростью.
  - **Concurrency** — ограничение одновременных запросов.
- `RateLimitPartition` — стратегия по ключу клиента (IP, API key).

## Health Checks
- Мониторинг состояния сервиса: `/health`, `/health/ready`, `/health/live`.
- `AddHealthChecks()` + проверки БД, кэша, внешних сервисов.
- **Liveness** — сервер жив? (базовый).
- **Readiness** — готов принимать трафик? (БД, кэш).
- Публикация через `MapHealthChecks()`, интеграция с Kubernetes probes.

## Middleware customisation
- `IApplicationBuilder` — кастомная логика через `Use`, `Map`, `When`.
- `Run` — терминальный middleware (не вызывает next).
- `Map` — ветвление по пути (`/admin` → своя цепочка).
- `UseWhen` — условное выполнение middleware.

## Важно для интервью
- Rate limiting vs throttling.
- `EnableRateLimiting` vs `DisableRateLimiting` фильтры.
- Разница Live/Readiness health checks для Kubernetes.
- Кастомный middleware — `InvokeAsync(HttpContext, RequestDelegate)`.
