## Интеграция с ASP.NET Core
- gRPC-сервисы хостятся в ASP.NET Core наравне с REST API.
- Поддержка через `AddGrpc()` и маршрутизацию через `MapGrpcService<T>()`.
- gRPC-Web — для браузерных клиентов (через proxy или без).
