## Hexagonal Architecture (Порты и Адаптеры)
- **Ports** — интерфейсы в core (inbound / outbound).
- **Adapters** — реализации этих интерфейсов (driven / driving).
- Driving adapters = API, контроллеры, входящие сообщения.
- Driven adapters = БД, message brokers, внешние вызовы.
