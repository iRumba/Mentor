## Channels
- **System.Threading.Tasks.Channels** (~.NET Core 3.0) — producer/consumer очередь с async поддержкой.
- **Channel<T>**:
  - `Channel.CreateBounded<T>(capacity)` — с ограничением размера (backpressure).
  - `Channel.CreateUnbounded<T>()` — без ограничений.
  - `WriteAsync` / `ReadAsync` / `TryWrite` / `TryRead`.
  - Поддерживает `IAsyncEnumerable<T>` через `Reader.ReadAllAsync()`.
- Используется для потоковой обработки данных, пайплайнов.
