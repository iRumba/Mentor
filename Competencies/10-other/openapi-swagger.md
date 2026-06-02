# OpenAPI / Swagger

## OpenAPI (OAS) / Swagger
- **OpenAPI Specification** — стандарт описания REST API (YAML/JSON).
- **Swagger** — набор инструментов от SmartBear (Swagger UI, Swagger Editor, Codegen).
- ASP.NET Core: `Swashbuckle.AspNetCore` или `Microsoft.AspNetCore.OpenApi`.

## Swashbuckle
- Стандартная интеграция: `AddSwaggerGen()` + `UseSwagger()` + `UseSwaggerUI()`.
- Автоматическая генерация OpenAPI-контракта из кода.
- Поддержка XML-комментариев для описания полей.
- `[SwaggerOperation]`, `[SwaggerResponse]` — уточнение документации.

## Microsoft.AspNetCore.OpenApi (.NET 9+)
- Трансформеры — трансформация документа OpenAPI (добавление параметров, заголовков).
- Трансформеры операций — изменение конкретных операций.
- Более тесная интеграция с Minimal API.

## API Versioning
- `Asp.Versioning.Http` / `Microsoft.AspNetCore.Mvc.Versioning` — для Controllers.
- Versioning via URL: `/api/v1/orders`, `/api/v2/orders`.
- Versioning via Header: `X-API-Version: 2`.
- Swagger с мультиверсиями — `AddSwaggerGen(c => { c.SwaggerDoc("v1", ...); c.SwaggerDoc("v2", ...); })`.

## Best Practices
- Документировать response codes (200, 201, 400, 401, 403, 500).
- Описывать error response (`ProblemDetails`).
- `[ProducesResponseType(typeof(T), 200)]` — типизированные ответы.
- Использовать `OpenApiInfo` для метаданных (описание, лицензия, контакт).

## Важно для интервью
- OpenAPI — язык для описания API, Swagger — инструменты.
- Client generation — `nswag` / `autorest` / `openapi-generator`.
- OpenAPI 3.0 vs 3.1 (поддержка JSON Schema).
