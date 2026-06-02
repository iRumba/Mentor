## Best Practices
- Документировать response codes (200, 201, 400, 401, 403, 500).
- Описывать error response (`ProblemDetails`).
- `[ProducesResponseType(typeof(T), 200)]` — типизированные ответы.
- Использовать `OpenApiInfo` для метаданных (описание, лицензия, контакт).
