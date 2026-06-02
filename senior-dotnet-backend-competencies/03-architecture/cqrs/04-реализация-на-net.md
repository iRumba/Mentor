## Реализация на .NET
- **MediatR** — популярная библиотека для CQRS: `IRequest<T>` и `IRequestHandler<T>`.
- Команды/запросы — отдельные классы, обработчики — отдельные классы.
- Pipeline behaviours — cross-cutting concerns (логирование, валидация, транзакции).
