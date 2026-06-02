## REST
- **Resource-based** — URL == ресурс (`/users`, `/users/1`).
- **HTTP методы**: GET (read), POST (create), PUT (replace), PATCH (update), DELETE.
- **Статусы**: 2xx (успех), 3xx (редирект), 4xx (ошибка клиента), 5xx (ошибка сервера).
- **HATEOAS** — гипермедиа как движок состояния (редко реализуется на практике).
- Best practices: пагинация, фильтрация, сортировка через query params.
