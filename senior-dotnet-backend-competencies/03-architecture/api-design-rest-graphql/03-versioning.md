## Versioning
- **URL-based**: `/api/v1/users` (простой, но нарушает REST идеологию).
- **Header-based**: `Accept: application/vnd.myapi.v1+json` (чистый REST, но менее прозрачный).
- **Query param**: `/api/users?version=1` (просто, но замусоривает URL).
