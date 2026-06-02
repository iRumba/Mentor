# API Design: REST, GraphQL, Versioning

## REST
- **Resource-based** — URL == ресурс (`/users`, `/users/1`).
- **HTTP методы**: GET (read), POST (create), PUT (replace), PATCH (update), DELETE.
- **Статусы**: 2xx (успех), 3xx (редирект), 4xx (ошибка клиента), 5xx (ошибка сервера).
- **HATEOAS** — гипермедиа как движок состояния (редко реализуется на практике).
- Best practices: пагинация, фильтрация, сортировка через query params.

## GraphQL
- Язык запросов от Facebook. Клиент сам указывает, какие поля нужны.
- **Single endpoint** (`POST /graphql`), вся логика в resolvers.
- Проблемы: N+1, сложное кэширование, авторизация на уровне полей.
- **Batch, DataLoader** — решение N+1 для .NET.

## Versioning
- **URL-based**: `/api/v1/users` (простой, но нарушает REST идеологию).
- **Header-based**: `Accept: application/vnd.myapi.v1+json` (чистый REST, но менее прозрачный).
- **Query param**: `/api/users?version=1` (просто, но замусоривает URL).

## Важно для интервью
- REST vs GraphQL — не конкуренты, а разные инструменты.
- Когда GraphQL: сложные клиентские требования, разные клиенты, агрегация.
- Когда REST: простота, кэширование, стабильный API.
- Breaking changes в API — расширять (добавлять поля), не менять.
