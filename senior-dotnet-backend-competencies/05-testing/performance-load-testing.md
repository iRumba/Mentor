# Performance / Load Testing

## NBomber
- Фреймворк для нагрузочного тестирования на .NET.
- Пишется на C# — тесты в том же языке, что и проект.
- **Step** — единица нагрузки (HTTP-запрос, DB query, gRPC).
- Поддержка Reporting (CSV, HTML, InfluxDB + Grafana).
- Анализ: OK/fail, latency, RPS, percentiles (p50, p75, p95, p99).

## k6
- Инструмент от Grafana Labs. Тесты пишутся на JavaScript.
- Высокая производительность (на Go).
- Интеграция с Grafana Cloud, Prometheus, InfluxDB.
- Хорош для HTTP/API нагрузочного тестирования.

## Типы тестов
- **Smoke** — минимальная нагрузка для проверки стабильности.
- **Load / Performance** — ожидаемая рабочая нагрузка.
- **Stress** — выше ожидаемой, чтобы найти предел.
- **Soak** — длительная нагрузка для выявления утечек памяти.
- **Spike** — резкий скачок нагрузки.

## Важно для интервью
- RPS (requests per second) vs Latency — главные метрики.
- Tail latency (p99) важнее средней.
- Всегда ставить SLA/SLO/RTO до тестирования.
- NBomber — подходит когда нужна интеграция с .NET-экосистемой.
