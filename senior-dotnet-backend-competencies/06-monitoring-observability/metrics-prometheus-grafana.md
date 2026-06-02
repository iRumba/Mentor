# Метрики: Prometheus, Grafana

## Prometheus
- Time-series БД для сбора и хранения метрик.
- Pull-модель: Prometheus сам забирает метрики (`/metrics` endpoint).
- **OpenTelemetry** — `AddPrometheusExporter()` для экспорта метрик.
- Типы метрик:
  - **Counter** — только увеличивается (число запросов).
  - **Gauge** — может увеличиваться/уменьшаться (число соединений, память).
  - **Histogram** — распределение значений (длительность запросов).
  - **Summary** — квантили на стороне клиента.

## Grafana
- Визуализация метрик из Prometheus (и других источников).
- Дашборды — графики, таблицы, алерты.
- Поддерживает аннотации, переменные, ad-hoc фильтры.
- Alerts — пороговые уведомления через Grafana Alerting.

## .NET метрики
- `dotnet-counters` — CLI утилита для сбора метрик.
- `System.Diagnostics.Metrics` — встроенный API (.NET 8+).
- Meter + Instrument + Counter/Histogram.
- `MeterProvider` — настройка через OpenTelemetry.

## Важно для интервью
- RED (Rate, Errors, Duration) и USE (Utilization, Saturation, Errors) метрики для сервисов.
- Четыре золотых сигнала (Google SRE): Latency, Traffic, Errors, Saturation.
- Rate (RPS) vs Duration (p95) — разные аспекты.
- Latency — использовать Histogram, не Gauge.
