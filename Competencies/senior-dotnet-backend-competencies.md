# Компетенции Senior Backend C# .NET Developer

## 1. Язык C# и .NET Platform

- Глубокое понимание CLR, GC, JIT, типов памяти (stack/heap)
- Value types vs reference types, boxing/unboxing, структуры
- async/await, TPL, Channels, Dataflow, IAsyncEnumerable
- Generics, covariance/contravariance, constraints
- Reflection, Emit, source generators, expressions trees
- Span\<T\>, Memory\<T\>, unsafe code, zero-copy
- LINQ (performance, Deferred Execution, IQueryable vs IEnumerable)
- Pattern matching, records, discriminated unions
- Интероп с нативным кодом (P/Invoke, COM)

## 2. ASP.NET Core

- Middleware pipeline, lifecycle запроса
- Dependency Injection (регистрация, Scope, контейнеры)
- Configuration API, Options pattern, PostConfigure
- Authentication/Authorization (JWT, cookies, policies, claims, roles)
- Filters (Authorization, Action, Exception, Result)
- Minimal API vs Controllers
- SignalR (real-time communication)
- gRPC (protobuf, interceptors, streaming)
- Rate limiting, health checks, middleware customisation

## 3. Архитектура и проектирование

- Domain-Driven Design (Entity, Value Object, Aggregate, Repository)
- Command Query Responsibility Segregation (CQRS)
- Event Sourcing, Event-driven architecture
- Clean Architecture / Hexagonal Architecture / Onion Architecture
- SOLID, DRY, YAGNI, KISS
- Dependency Injection, IoC-контейнеры (Autofac, Scrutor)
- Message brokers (RabbitMQ, Kafka, Azure Service Bus)
- Saga pattern, Outbox pattern, Circuit Breaker
- API design (REST, GraphQL, versioning)

## 4. Базы данных

- **Реляционные**: SQL Server, PostgreSQL (индексы, планы, оконные функции, CTE)
- ORM: Entity Framework Core (включая Performance, NoTracking, Compiled Queries, Raw SQL)
- Dapper (ручная оптимизация запросов)
- **NoSQL**: MongoDB, Redis (структуры данных, Pub/Sub, кэширование)
- Elasticsearch (индексация, поиск, агрегации)

## 5. Тестирование

- Unit-тесты: xUnit / NUnit, Moq / NSubstitute, FluentAssertions
- Интеграционные тесты (TestContainers, WebApplicationFactory)
- Автоматизация тестов (SpecFlow / Reqnroll)
- Performance / load testing (NBomber, k6)

## 6. Мониторинг и Observability

- Structured logging (Serilog)
- Distributed tracing (OpenTelemetry, Jaeger, Zipkin)
- Метрики (Prometheus, Grafana)
- Health checks, алертинг

## 7. CI/CD и DevOps

- Docker (Dockerfile, multi-stage, compose)
- CI/CD pipelines (GitHub Actions, Azure DevOps, GitLab CI)
- Kubernetes (Deployment, Service, ConfigMap, Sealed Secrets)
- Infrastructure as Code (Terraform, Bicep, Pulumi)
- Feature flags (LaunchDarkly, Unleash)

## 8. Безопасность

- OWASP Top 10 и типовые уязвимости
- Secret management (Azure Key Vault, HashiCorp Vault)
- OAuth 2.0 / OpenID Connect
- SQL injection, XSS, CSRF защиты
- Secure coding practices

## 9. Soft Skills

- Код-ревью (конструктивная обратная связь)
- Менторство (junior/middle, onboarding, growth plans)
- Технические спеки и RFC (Tech Design Document, ADR)
- Оценка сложности и декомпозиция задач
- Коммуникация с заказчиком и внутри команды
- Проведение технических интервью

## 10. Прочее

- Профилирование и оптимизация производительности (dotTrace, PerfView)
- Миграции и breaking changes (старого кода, версий .NET, БД)
- Работа с легаси (рефакторинг, постепенная миграция, Strangler Fig)
- OpenAPI / Swagger, API версионирование
- Документирование кода и архитектуры
- Code style, analyzers, Roslyn
