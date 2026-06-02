# Distributed Tracing (OpenTelemetry, Jaeger, Zipkin)

## Что такое Distributed Tracing
- Отслеживание запроса через несколько микросервисов.
- **Trace** — дерево из span'ов (единиц работы).
- **Span** — операция в одном сервисе (SQL, HTTP-вызов, очередь).

## OpenTelemetry (OTel)
- Стандарт для сбора трассировок, метрик и логов.
- Vendor-agnostic: данные можно отправлять в Jaeger, Zipkin, Prometheus, Application Insights.
- `AddOpenTelemetry()` — интеграция с ASP.NET Core.
- **Instrumentation** — автоматический сбор для HTTP, gRPC, EF Core, Redis.
- **Exporter** — куда отправляем: Console, OTLP, Jaeger, Zipkin.

## Jaeger / Zipkin
- **Jaeger** — распределённая трассировка от Uber. UI для поиска и визуализации.
- **Zipkin** — аналогичный инструмент от Twitter.
- Хранят span'ы, позволяют искать по service, operation, tags.

## Correlation ID
- `RequestId` / `CorrelationId` — проброс через заголовки HTTP.
- `Activity` (System.Diagnostics) — встроенный механизм для Distributed Tracing.
- W3C Trace Context (`traceparent` header) — стандарт.

## Важно для интервью
- OpenTelemetry — сегодня стандарт, не Jaeger/Zipkin напрямую.
- Sampling (head-based, tail-based) — для снижения объёма.
- Baggage propagation — передача контекста между сервисами.
- Trace ID + Span ID + Parent Span ID — структура трейса.
