# Event Sourcing, Event-Driven Architecture

## Event Sourcing
- Сохраняем не текущее состояние, а последовательность событий, которые к нему привели.
- **Event Store** — специальное хранилище (append-only). События не удаляются и не изменяются.
- **Projection** — текущее состояние, построенное из событий (может быть в отдельной БД).
- Позволяет получить состояние на любой момент времени (snapshot).

## Event-Driven Architecture
- Асинхронная коммуникация через события между сервисами.
- **Event Bus / Message Broker** — RabbitMQ, Kafka, Azure Service Bus, NATS.
- **Publish/Subscribe** — издатель не знает подписчиков.
- **События** бывают:
  - *Domain Event* — важное бизнес-событие (OrderSubmitted).
  - *Integration Event* — событие для других сервисов.

## Плюсы и минусы
| + | - |
|---|---|
| Аудит и traceability | Сложность |
| Гибкость добавления read моделей | Event versioning |
| Consistency в распределённых системах | Размер хранилища (нужен compaction) |

## Важно для интервью
- Choreography vs Orchestration (Saga).
- Exactly-once delivery vs at-least-once.
- Idempotent handlers — обязательное требование.
- Категоризация событий (event versioning, schema registry).
