## Реализация CQRS на .NET

### Основной стек: MediatR
В экосистеме .NET стандартом де-факто для реализации CQRS является библиотека **MediatR**. Она реализует паттерн "Посредник", позволяя полностью развязать отправителя запроса и его обработчика.

**Ключевые компоненты:**
- `IRequest<TResponse>`: Маркер для команды или запроса.
- `IRequestHandler<TRequest, TResponse>`: Класс, содержащий логику обработки.
- `IMediator`: Интерфейс для отправки запроса.

### Pipeline Behaviours (Перекрестная функциональность)
Одной из сильнейших сторон MediatR являются `IPipelineBehavior`. Это позволяет реализовать Aspect-Oriented Programming (AOP) без засорения бизнес-логики:
- **Валидация**: Создать один behavior, который автоматически вызывает FluentValidation для всех команд перед их обработкой.
- **Логирование**: Автоматически логировать каждый входящий запрос и время его выполнения.
- **Транзакции**: Обернуть выполнение команды в одну транзакцию БД.
- **Кэширование**: Проверять наличие данных в кэше перед тем, как передать запрос обработчику.

### Инструменты для продвинутого CQRS
- **Масштабирование чтения**: Использование `Dapper` для Query-запросов и `EF Core` для Command-запросов.
- **Событийная шина**: **MassTransit** или **Rebus** для передачи событий между Write и Read моделями в распределенных системах.
- **Хранилища событий**: Marten (на базе PostgreSQL), EventStoreDB.

### Пример структуры проекта
```csharp
// Command
public record CreateOrderCommand(Guid CustomerId, List<OrderItemDto> Items) : IRequest<Guid>;

// Handler
public class CreateOrderHandler : IRequestHandler<CreateOrderCommand, Guid> {
    public async Task<Guid> Handle(CreateOrderCommand request, CancellationToken ct) {
        // 1. Валидация
        // 2. Создание Domain Entity
        // 3. Сохранение в БД
        return orderId;
    }
}

// Query
public record GetOrderDetailsQuery(Guid OrderId) : IRequest<OrderDetailsDto>;
```

