# Компетенции Senior Backend C# .NET Developer

## 1. Язык C# и .NET Platform

- [Глубокое понимание CLR, GC, JIT, типов памяти (stack/heap)](01-csharp-dotnet/01-clr-gc-jit-memory.md)
- [Value types vs reference types, boxing/unboxing, структуры](01-csharp-dotnet/02-value-types-reference-types.md)
- [async/await, TPL, Channels, Dataflow, IAsyncEnumerable](01-csharp-dotnet/03-async-await-tpl-channels.md)
- [Generics, covariance/contravariance, constraints](01-csharp-dotnet/04-generics-covariance-contravariance.md)
- [Reflection, Emit, source generators, expressions trees](01-csharp-dotnet/05-reflection-emit-source-generators.md)
- [Span\<T\>, Memory\<T\>, unsafe code, zero-copy](01-csharp-dotnet/06-span-memory-unsafe.md)
- [LINQ (performance, Deferred Execution, IQueryable vs IEnumerable)](01-csharp-dotnet/07-linq-performance.md)
- [Pattern matching, records, discriminated unions](01-csharp-dotnet/08-pattern-matching-records.md)
- [Интероп с нативным кодом (P/Invoke, COM)](01-csharp-dotnet/09-interop-pinvoke-com.md)

## 2. ASP.NET Core

- [Middleware pipeline, lifecycle запроса](02-aspnet-core/middleware-pipeline-lifecycle.md)
- [Dependency Injection (регистрация, Scope, контейнеры)](02-aspnet-core/dependency-injection.md)
- [Configuration API, Options pattern, PostConfigure](02-aspnet-core/configuration-options-pattern.md)
- [Authentication/Authorization (JWT, cookies, policies, claims, roles)](02-aspnet-core/authentication-authorization-jwt.md)
- [Filters (Authorization, Action, Exception, Result)](02-aspnet-core/filters.md)
- [Minimal API vs Controllers](02-aspnet-core/minimal-api-vs-controllers.md)
- [SignalR (real-time communication)](02-aspnet-core/signalr.md)
- [gRPC (protobuf, interceptors, streaming)](02-aspnet-core/grpc.md)
- [Rate limiting, health checks, middleware customisation](02-aspnet-core/rate-limiting-health-checks.md)

## 3. Архитектура и проектирование

- [Domain-Driven Design (Entity, Value Object, Aggregate, Repository)](03-architecture/domain-driven-design.md)
- [Command Query Responsibility Segregation (CQRS)](03-architecture/cqrs.md)
- [Event Sourcing, Event-driven architecture](03-architecture/event-sourcing-event-driven.md)
- [Clean Architecture / Hexagonal Architecture / Onion Architecture](03-architecture/clean-hexagonal-onion-architecture.md)
- [SOLID, DRY, YAGNI, KISS](03-architecture/solid-dry-yagni-kiss.md)
- [Dependency Injection, IoC-контейнеры (Autofac, Scrutor)](03-architecture/dependency-injection-ioc.md)
- [Message brokers (RabbitMQ, Kafka, Azure Service Bus)](03-architecture/message-brokers.md)
- [Saga pattern, Outbox pattern, Circuit Breaker](03-architecture/saga-outbox-circuit-breaker.md)
- [API design (REST, GraphQL, versioning)](03-architecture/api-design-rest-graphql.md)

## 4. Базы данных

- [**Реляционные**: SQL Server, PostgreSQL (индексы, планы, оконные функции, CTE)](04-databases/relational-sql-server-postgresql.md)
- [ORM: Entity Framework Core (включая Performance, NoTracking, Compiled Queries, Raw SQL)](04-databases/entity-framework-core.md)
- [Dapper (ручная оптимизация запросов)](04-databases/dapper.md)
- [**NoSQL**: MongoDB, Redis (структуры данных, Pub/Sub, кэширование)](04-databases/nosql-mongodb-redis.md)
- [Elasticsearch (индексация, поиск, агрегации)](04-databases/elasticsearch.md)

## 5. Тестирование

- [Unit-тесты: xUnit / NUnit, Moq / NSubstitute, FluentAssertions](05-testing/unit-tests-xunit-nunit.md)
- [Интеграционные тесты (TestContainers, WebApplicationFactory)](05-testing/integration-tests.md)
- [Автоматизация тестов (SpecFlow / Reqnroll)](05-testing/automation-tests-specflow.md)
- [Performance / load testing (NBomber, k6)](05-testing/performance-load-testing.md)

## 6. Мониторинг и Observability

- [Structured logging (Serilog)](06-monitoring-observability/structured-logging-serilog.md)
- [Distributed tracing (OpenTelemetry, Jaeger, Zipkin)](06-monitoring-observability/distributed-tracing-opentelemetry.md)
- [Метрики (Prometheus, Grafana)](06-monitoring-observability/metrics-prometheus-grafana.md)
- [Health checks, алертинг](06-monitoring-observability/health-checks-alerting.md)

## 7. CI/CD и DevOps

- [Docker (Dockerfile, multi-stage, compose)](07-cicd-devops/docker.md)
- [CI/CD pipelines (GitHub Actions, Azure DevOps, GitLab CI)](07-cicd-devops/ci-cd-pipelines.md)
- [Kubernetes (Deployment, Service, ConfigMap, Sealed Secrets)](07-cicd-devops/kubernetes.md)
- [Infrastructure as Code (Terraform, Bicep, Pulumi)](07-cicd-devops/infrastructure-as-code.md)
- [Feature flags (LaunchDarkly, Unleash)](07-cicd-devops/feature-flags.md)

## 8. Безопасность

- [OWASP Top 10 и типовые уязвимости](08-security/owasp-top-10.md)
- [Secret management (Azure Key Vault, HashiCorp Vault)](08-security/secret-management.md)
- [OAuth 2.0 / OpenID Connect](08-security/oauth2-openid-connect.md)
- [SQL injection, XSS, CSRF защиты](08-security/sql-injection-xss-csrf.md)
- [Secure coding practices](08-security/secure-coding-practices.md)

## 9. Soft Skills

- [Код-ревью (конструктивная обратная связь)](09-soft-skills/code-review.md)
- [Менторство (junior/middle, onboarding, growth plans)](09-soft-skills/mentoring.md)
- [Технические спеки и RFC (Tech Design Document, ADR)](09-soft-skills/tech-specs-rfc.md)
- [Оценка сложности и декомпозиция задач](09-soft-skills/estimation-decomposition.md)
- [Коммуникация с заказчиком и внутри команды](09-soft-skills/communication.md)
- [Проведение технических интервью](09-soft-skills/technical-interviews.md)

## 10. Прочее

- [Профилирование и оптимизация производительности (dotTrace, PerfView)](10-other/profiling-performance.md)
- [Миграции и breaking changes (старого кода, версий .NET, БД)](10-other/migrations-breaking-changes.md)
- [Работа с легаси (рефакторинг, постепенная миграция, Strangler Fig)](10-other/legacy-strangler-fig.md)
- [OpenAPI / Swagger, API версионирование](10-other/openapi-swagger.md)
- [Документирование кода и архитектуры](10-other/documentation.md)
- [Code style, analyzers, Roslyn](10-other/code-style-analyzers-roslyn.md)
