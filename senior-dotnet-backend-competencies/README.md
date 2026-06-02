# Компетенции Senior Backend C# .NET Developer

## 1. Язык C# и .NET Platform

- [Глубокое понимание CLR, GC, JIT, типов памяти (stack/heap)](01-csharp-dotnet/01-clr-gc-jit-memory/)
- [Value types vs reference types, boxing/unboxing, структуры](01-csharp-dotnet/02-value-types-reference-types/)
- [async/await, TPL, Channels, Dataflow, IAsyncEnumerable](01-csharp-dotnet/03-async-await-tpl-channels/)
- [Generics, covariance/contravariance, constraints](01-csharp-dotnet/04-generics-covariance-contravariance/)
- [Reflection, Emit, source generators, expressions trees](01-csharp-dotnet/05-reflection-emit-source-generators/)
- [Span\<T\>, Memory\<T\>, unsafe code, zero-copy](01-csharp-dotnet/06-span-memory-unsafe/)
- [LINQ (performance, Deferred Execution, IQueryable vs IEnumerable)](01-csharp-dotnet/07-linq-performance/)
- [Pattern matching, records, discriminated unions](01-csharp-dotnet/08-pattern-matching-records/)
- [Интероп с нативным кодом (P/Invoke, COM)](01-csharp-dotnet/09-interop-pinvoke-com/)

## 2. ASP.NET Core

- [Middleware pipeline, lifecycle запроса](02-aspnet-core/middleware-pipeline-lifecycle/)
- [Dependency Injection (регистрация, Scope, контейнеры)](02-aspnet-core/dependency-injection/)
- [Configuration API, Options pattern, PostConfigure](02-aspnet-core/configuration-options-pattern/)
- [Authentication/Authorization (JWT, cookies, policies, claims, roles)](02-aspnet-core/authentication-authorization-jwt/)
- [Filters (Authorization, Action, Exception, Result)](02-aspnet-core/filters/)
- [Minimal API vs Controllers](02-aspnet-core/minimal-api-vs-controllers/)
- [SignalR (real-time communication)](02-aspnet-core/signalr/)
- [gRPC (protobuf, interceptors, streaming)](02-aspnet-core/grpc/)
- [Rate limiting, health checks, middleware customisation](02-aspnet-core/rate-limiting-health-checks/)

## 3. Архитектура и проектирование

- [Domain-Driven Design (Entity, Value Object, Aggregate, Repository)](03-architecture/domain-driven-design/)
- [Command Query Responsibility Segregation (CQRS)](03-architecture/cqrs/)
- [Event Sourcing, Event-driven architecture](03-architecture/event-sourcing-event-driven/)
- [Clean Architecture / Hexagonal Architecture / Onion Architecture](03-architecture/clean-hexagonal-onion-architecture/)
- [SOLID, DRY, YAGNI, KISS](03-architecture/solid-dry-yagni-kiss/)
- [Dependency Injection, IoC-контейнеры (Autofac, Scrutor)](03-architecture/dependency-injection-ioc/)
- [Message brokers (RabbitMQ, Kafka, Azure Service Bus)](03-architecture/message-brokers/)
- [Saga pattern, Outbox pattern, Circuit Breaker](03-architecture/saga-outbox-circuit-breaker/)
- [API design (REST, GraphQL, versioning)](03-architecture/api-design-rest-graphql/)

## 4. Базы данных

- [**Реляционные**: SQL Server, PostgreSQL (индексы, планы, оконные функции, CTE)](04-databases/relational-sql-server-postgresql/)
- [ORM: Entity Framework Core (включая Performance, NoTracking, Compiled Queries, Raw SQL)](04-databases/entity-framework-core/)
- [Dapper (ручная оптимизация запросов)](04-databases/dapper/)
- [**NoSQL**: MongoDB, Redis (структуры данных, Pub/Sub, кэширование)](04-databases/nosql-mongodb-redis/)
- [Elasticsearch (индексация, поиск, агрегации)](04-databases/elasticsearch/)

## 5. Тестирование

- [Unit-тесты: xUnit / NUnit, Moq / NSubstitute, FluentAssertions](05-testing/unit-tests-xunit-nunit/)
- [Интеграционные тесты (TestContainers, WebApplicationFactory)](05-testing/integration-tests/)
- [Автоматизация тестов (SpecFlow / Reqnroll)](05-testing/automation-tests-specflow/)
- [Performance / load testing (NBomber, k6)](05-testing/performance-load-testing/)

## 6. Мониторинг и Observability

- [Structured logging (Serilog)](06-monitoring-observability/structured-logging-serilog/)
- [Distributed tracing (OpenTelemetry, Jaeger, Zipkin)](06-monitoring-observability/distributed-tracing-opentelemetry/)
- [Метрики (Prometheus, Grafana)](06-monitoring-observability/metrics-prometheus-grafana/)
- [Health checks, алертинг](06-monitoring-observability/health-checks-alerting/)

## 7. CI/CD и DevOps

- [Docker (Dockerfile, multi-stage, compose)](07-cicd-devops/docker/)
- [CI/CD pipelines (GitHub Actions, Azure DevOps, GitLab CI)](07-cicd-devops/ci-cd-pipelines/)
- [Kubernetes (Deployment, Service, ConfigMap, Sealed Secrets)](07-cicd-devops/kubernetes/)
- [Infrastructure as Code (Terraform, Bicep, Pulumi)](07-cicd-devops/infrastructure-as-code/)
- [Feature flags (LaunchDarkly, Unleash)](07-cicd-devops/feature-flags/)

## 8. Безопасность

- [OWASP Top 10 и типовые уязвимости](08-security/owasp-top-10/)
- [Secret management (Azure Key Vault, HashiCorp Vault)](08-security/secret-management/)
- [OAuth 2.0 / OpenID Connect](08-security/oauth2-openid-connect/)
- [SQL injection, XSS, CSRF защиты](08-security/sql-injection-xss-csrf/)
- [Secure coding practices](08-security/secure-coding-practices/)

## 9. Soft Skills

- [Код-ревью (конструктивная обратная связь)](09-soft-skills/code-review/)
- [Менторство (junior/middle, onboarding, growth plans)](09-soft-skills/mentoring/)
- [Технические спеки и RFC (Tech Design Document, ADR)](09-soft-skills/tech-specs-rfc/)
- [Оценка сложности и декомпозиция задач](09-soft-skills/estimation-decomposition/)
- [Коммуникация с заказчиком и внутри команды](09-soft-skills/communication/)
- [Проведение технических интервью](09-soft-skills/technical-interviews/)

## 10. Прочее

- [Профилирование и оптимизация производительности (dotTrace, PerfView)](10-other/profiling-performance/)
- [Миграции и breaking changes (старого кода, версий .NET, БД)](10-other/migrations-breaking-changes/)
- [Работа с легаси (рефакторинг, постепенная миграция, Strangler Fig)](10-other/legacy-strangler-fig/)
- [OpenAPI / Swagger, API версионирование](10-other/openapi-swagger/)
- [Документирование кода и архитектуры](10-other/documentation/)
- [Code style, analyzers, Roslyn](10-other/code-style-analyzers-roslyn/)
