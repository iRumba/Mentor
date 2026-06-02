# SignalR (Real-time communication)

## Что такое SignalR
- Библиотека для real-time веб-функциональности — сервер может отправлять данные клиентам мгновенно.
- Абстрагирует транспорт: WebSockets (основной), Server-Sent Events, Long Polling.
- Поддерживает .NET клиент, JavaScript/TypeScript клиент, Blazor.

## Основные концепции
- **Hub** — центральный класс, принимающий вызовы от клиентов и отправляющий сообщения.
- `Clients.All.SendAsync("Method", data)` — всем клиентам.
- `Clients.Group("group").SendAsync(...)` — группе.
- `Clients.Caller.SendAsync(...)` — отправителю.
- `Clients.User(userId).SendAsync(...)` — конкретному пользователю.

## Groups
- `Groups.AddToGroupAsync(connectionId, groupName)` — управление группами.
- Автоматическое удаление из группы при отключении.

## Scaling (масштабирование)
- SignalR работает в рамках одного процесса. Для фермы (несколько инстансов) нужен **backplane**:
  - Azure SignalR Service.
  - Redis backplane (`Microsoft.AspNetCore.SignalR.StackExchangeRedis`).
  - RabbitMQ / custom.

## Важно для интервью
- Negotiation — клиент запрашивает доступные транспорты, выбирает наилучший.
- `HubConnectionContext` — жизненный цикл соединения.
- `IHostedService` + SignalR — фоновые уведомления клиентов.
- Strongly-typed hubs — интерфейс вместо строковых методов.
