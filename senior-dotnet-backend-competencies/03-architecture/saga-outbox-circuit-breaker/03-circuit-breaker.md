## Circuit Breaker
- Защита от каскадных сбоев: если сервис падает, прекращаем вызовы и возвращаем fallback.
- **Состояния**: Closed (работает) → Open (не вызываем) → Half-Open (пробный вызов).
- `Polly` — основная библиотека для .NET: `CircuitBreakerPolicy`, `RetryPolicy`.
- Комбинируется с Retry (отличается по цели: retry — временная ошибка, circuit breaker — защита).
