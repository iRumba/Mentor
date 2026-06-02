# NoSQL: MongoDB, Redis

## MongoDB (Document Store)
- **Документная БД** — JSON-like документы (BSON), без схемы (schema-less).
- Хороша для: гибкие модели данных, быстрая разработка, кэш, логи, content management.
- Агрегации — pipeline для трансформации данных (`$match`, `$group`, `$lookup`).
- Индексы: одиночные, составные, текстовые, TTL, geo-spatial.
- **Replica Set** — отказоустойчивость. **Sharding** — масштабирование.

## Redis (Key-Value Store / Cache)
- Данные в памяти (in-memory). Миллионы операций/сек.
- **Структуры данных**: String, List, Set, Sorted Set, Hash, Bitmap, HyperLogLog, Stream.
- **Pub/Sub** — лёгкая система сообщений (one-to-many, fire-and-forget).
- **Кэширование** — распределённый кэш (IDistributedCache). TTL, eviction policies (LRU, LFU, TTL).

## Когда что использовать
| | MongoDB | Redis |
|---|---|---|
| Persistent? | Да (на диск) | Опционально (snapshot/AOF) |
| Объём | Большие данные | Всё в памяти |
| Сложные запросы | Агрегации, индексы | Только по ключу |

## Важно для интервью
- MongoDB — транзакции (с версии 4.0, multi-document).
- Redis — clustering, sentinel для HA.
- Структуры данных Redis — Sorted Set (лидерборды), HyperLogLog (уникальные посетители).
- Кэширование: Cache-aside vs Read-through (стратегии).
