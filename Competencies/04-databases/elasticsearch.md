# Elasticsearch

## Что такое Elasticsearch
- Распределённая поисковая и аналитическая система на базе Apache Lucene.
- Хранение в JSON-документах, полнотекстовый поиск, агрегации.
- ELK Stack: Elasticsearch + Logstash + Kibana.

## Индексация
- **Index** — аналог БД/таблицы. **Document** — строка.
- **Mapping** — схема полей (явная или динамическая).
- **Inverted Index** — обратный индекс для быстрого полнотекстового поиска.
- **Shard** — часть индекса (горизонтальное масштабирование). **Replica** — копия шарда.

## Поиск
- **Query DSL** — JSON-запросы на поиск: `match`, `term`, `range`, `bool`.
- **Full-text search** — `match`, `match_phrase`, `multi_match`.
- **Exact search** — `term`, `terms`, `exists`.
- **Fuzzy search** — опечатки (fuzziness, n-grams, edge n-grams).

## Агрегации
- **Metric** — min, max, avg, sum, cardinality.
- **Bucket** — группировка (date histogram, terms, range).
- **Pipeline** — цепочка агрегаций.

## Важно для интервью
- Elasticsearch не транзакционная БД — eventual consistency.
- Nested vs Join (parent/child) — производительность.
- Индексация по расписанию vs near-real-time (refresh_interval).
- Когда Elasticsearch: поиск, логирование, аналитика, full-text search.
