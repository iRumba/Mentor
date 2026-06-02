## OpenTelemetry (OTel)
- Стандарт для сбора трассировок, метрик и логов.
- Vendor-agnostic: данные можно отправлять в Jaeger, Zipkin, Prometheus, Application Insights.
- `AddOpenTelemetry()` — интеграция с ASP.NET Core.
- **Instrumentation** — автоматический сбор для HTTP, gRPC, EF Core, Redis.
- **Exporter** — куда отправляем: Console, OTLP, Jaeger, Zipkin.
