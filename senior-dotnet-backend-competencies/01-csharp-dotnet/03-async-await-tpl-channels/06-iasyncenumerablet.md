## IAsyncEnumerable<T>
- Асинхронный аналог IEnumerable<T> (C# 8.0).
- Позволяет возвращать элементы по мере их поступления с await:
  ```csharp
  await foreach (var item in GetAsyncSequence())
  ```
- Используется для потоковой передачи данных (gRPC streaming, чтение больших файлов, Kafka consumer).
