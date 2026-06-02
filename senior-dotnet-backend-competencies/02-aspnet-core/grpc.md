# gRPC

## Что такое gRPC
- High-performance RPC-фреймворк от Google. Использует HTTP/2, Protocol Buffers (protobuf).
- Подходит для server-to-server коммуникации (внутренние микросервисы).

## Protocol Buffers (protobuf)
- Язык определения интерфейсов (IDL) — `.proto` файлы.
- Двоичная сериализация — компактнее и быстрее JSON/XML.
- Генерация типизированных клиентов и серверов из `.proto`.

## Типы gRPC-методов
- **Unary** — запрос → ответ (как обычный HTTP).
- **Server streaming** — запрос → поток ответов.
- **Client streaming** — поток запросов → один ответ.
- **Bidirectional streaming** — два независимых потока.

## Interceptors
- Аналог middleware для gRPC — логирование, auth, метрики.
- Работают на уровне вызова RPC, до/после обработчика.

## Интеграция с ASP.NET Core
- gRPC-сервисы хостятся в ASP.NET Core наравне с REST API.
- Поддержка через `AddGrpc()` и маршрутизацию через `MapGrpcService<T>()`.
- gRPC-Web — для браузерных клиентов (через proxy или без).

## Важно для интервью
- Когда gRPC вместо REST: низкая latency, строгий контракт, streaming.
- Deadline и CancellationToken — timeout на стороне клиента.
- Deadline propagation — проброс через контекст.
- Load balancing — gRPC требует L7 (HTTP/2 multiplexing) или client-side LB.
