# Clean / Hexagonal / Onion Architecture

## Общая идея
- Все три архитектуры реализуют **Dependency Inversion**: внешние слои (БД, UI, API) зависят от внутренних (core/domain), а не наоборот.
- Core (domain) не зависит ни от чего, содержит бизнес-логику.
- Тестирование без инфраструктуры — core можно покрыть unit-тестами.

## Onion Architecture (Луковая)
- **Domain Models** — центр.
- **Domain Services** — вокруг.
- **Application Services** — use cases.
- **Infrastructure** — БД, внешние API.
- **UI/API** — самый внешний слой.

## Hexagonal Architecture (Порты и Адаптеры)
- **Ports** — интерфейсы в core (inbound / outbound).
- **Adapters** — реализации этих интерфейсов (driven / driving).
- Driving adapters = API, контроллеры, входящие сообщения.
- Driven adapters = БД, message brokers, внешние вызовы.

## Clean Architecture (Чистая)
- Аналогична луковой с акцентом на use cases.
- **Entities** → **Use Cases** → **Interface Adapters** → **Frameworks**.
- Правило зависимостей: внешний круг может зависеть от внутреннего, но не наоборот.

## Важно для интервью
- Все три — варианты одной идеи (Dependency Inversion + разделение слоёв).
- Core не должен иметь ссылок на `Newtonsoft.Json`, `EF Core`, `SQL Server`.
- `IOrderRepository` в core, `OrderRepository : IOrderRepository` в Infrastructure.
- Компромисс: больше кода (интерфейсы, DTO, маппинг).
