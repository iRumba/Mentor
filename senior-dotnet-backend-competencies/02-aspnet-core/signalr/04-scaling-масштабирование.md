## Scaling (масштабирование)
- SignalR работает в рамках одного процесса. Для фермы (несколько инстансов) нужен **backplane**:
  - Azure SignalR Service.
  - Redis backplane (`Microsoft.AspNetCore.SignalR.StackExchangeRedis`).
  - RabbitMQ / custom.
