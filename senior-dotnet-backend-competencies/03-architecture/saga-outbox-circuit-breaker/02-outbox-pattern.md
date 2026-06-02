## Outbox Pattern
- Решает проблему атомарности между БД и message broker.
- Сохраняем событие в ту же БД (таблица Outbox) в той же транзакции, что и бизнес-данные.
- Outbox processor отправляет события в брокер (Idempotent, resilient).
- Варианты: Polling + Background Service, Transactional Outbox + CDC (Debezium).
