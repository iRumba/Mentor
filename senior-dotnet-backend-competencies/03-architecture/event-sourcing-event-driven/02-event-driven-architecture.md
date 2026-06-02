## Event-Driven Architecture
- Асинхронная коммуникация через события между сервисами.
- **Event Bus / Message Broker** — RabbitMQ, Kafka, Azure Service Bus, NATS.
- **Publish/Subscribe** — издатель не знает подписчиков.
- **События** бывают:
  - *Domain Event* — важное бизнес-событие (OrderSubmitted).
  - *Integration Event* — событие для других сервисов.
