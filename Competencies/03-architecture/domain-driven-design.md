# Domain-Driven Design (DDD)

## Основные концепции
- **Entity** — объект с уникальным идентификатором (Id). Изменяется, но Id не меняется.
- **Value Object** — неизменяемый объект без Id, определяется своими атрибутами (деньги, адрес).
- **Aggregate** — группа Entity и Value Object, с одним корнем (Aggregate Root). Внешние ссылки только на корень.
- **Repository** — абстракция доступа к данным, коллекция Aggregate Root'ов.

## Стратегическое проектирование
- **Bounded Context** — граница модели (микросервис, модуль). В каждом контексте — свой язык.
- **Ubiquitous Language** — единый язык между разработчиками и экспертами.
- **Context Map** — отношения между Bounded Context'ами (Customer/Supplier, Shared Kernel, Anti-Corruption Layer).

## Тактическое проектирование
- **Domain Service** — бизнес-логика, не помещающаяся в Entity/Value Object.
- **Domain Event** — событие, которое произошло в домене (OrderPlaced).
- **Specification** — бизнес-правило (клиент имеет право на кредит).

## Важно для интервью
- Anemic Domain Model vs Rich Domain Model — первое антипаттерн.
- DDD не обязателен везде — оправдан для сложной бизнес-логики.
- Dependency Inversion: Domain layer не зависит от Infrastructure.
- Отличие Entity от Value Object — по идентификатору.
