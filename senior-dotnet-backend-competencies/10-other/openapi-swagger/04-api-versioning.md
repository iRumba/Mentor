## API Versioning
- `Asp.Versioning.Http` / `Microsoft.AspNetCore.Mvc.Versioning` — для Controllers.
- Versioning via URL: `/api/v1/orders`, `/api/v2/orders`.
- Versioning via Header: `X-API-Version: 2`.
- Swagger с мультиверсиями — `AddSwaggerGen(c => { c.SwaggerDoc("v1", ...); c.SwaggerDoc("v2", ...); })`.
