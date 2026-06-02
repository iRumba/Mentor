# Message Brokers (RabbitMQ, Kafka, Azure Service Bus)

## RabbitMQ
- **Традиционный брокер сообщений** — очередь сообщений с exchange/routing.
- Поддерживает гарантированную доставку, подтверждения, DLQ.
- Хорош для: task queues, RPC, умеренные нагрузки.
- Exchange types: Direct, Topic, Fanout, Headers.

## Apache Kafka
- **Event streaming platform** — распределённый, устойчивый, высокопроизводительный.
- Сообщения хранятся в topic'ах, партиционируются и реплицируются.
- Consumer groups — параллельная обработка с гарантией порядка внутри партиции.
- Хорош для: event sourcing, stream processing, высокая пропускная способность.

## Azure Service Bus
- Облачный брокер с интеграцией в Azure ecosystem.
- **Queues** (point-to-point) и **Topics** (pub/sub) с фильтрами SQL.
- Поддержка Session, Scheduled messages, dead-lettering.

## Сравнение
| | RabbitMQ | Kafka | ASB |
|---|---|---|---|
| Модель | Queue/Pub-Sub | Log | Queue/Topic |
| Порядок | FIFO (один consumer) | Внутри партиции | FIFO в сессии |
| Хранение | Удаляет после ACK | Retention-based | TTL-based |

## Важно для интервью
- Когда Kafka, когда RabbitMQ — разное назначение (брокер vs потоковый процессор).
- Гарантии: at-most-once, at-least-once, exactly-once.
- Delivery vs acknowledgment semantics.
