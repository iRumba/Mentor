# Интеграционные тесты

## WebApplicationFactory
- `WebApplicationFactory<T>` — создаёт in-memory экземпляр приложения.
- `HttpClient` для HTTP-запросов к приложению.
- `ConfigureWebHost()` — подмена зависимостей на тестовые/фейковые.
- NuGet: `Microsoft.AspNetCore.Mvc.Testing`.

## TestContainers
- Запуск реальных контейнеров (БД, Redis, Kafka) в Docker для тестов.
- **Testcontainers for .NET** — библиотека для управления containers в тестовом lifecycle.
- `TestcontainersSettings.ResourceReaper` — авто-чистка контейнеров.
- Поддерживает: SQL Server, PostgreSQL, Redis, Kafka, Azurite, LocalStack.

## Integration тесты vs Unit тесты
- Unit — изолированный класс (моки).
- Integration — реальная инфраструктура (БД, кэш, external API).
- Integration медленнее, но дают больше уверенности.

## Важно для интервью
- Подход тестировать через реальный HTTP + TestContainers даёт наибольшую уверенность.
- `CollectionFixture` — shared контейнер для всех тестов в коллекции.
- Seed data для каждого теста (clean state).
- Startup overhead — TestContainers запускают Docker, первый тест медленный.
