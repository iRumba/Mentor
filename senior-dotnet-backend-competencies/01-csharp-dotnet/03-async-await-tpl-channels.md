# async/await, TPL, Channels, Dataflow, IAsyncEnumerable

## async/await
- **async** — модификатор метода, позволяющий использовать await.
- **await** — приостанавливает выполнение метода до завершения ожидаемой задачи (Task), не блокируя поток.
- **State Machine** — компилятор генерирует структуру конечного автомата, которая управляет выполнением асинхронного метода.
- **SynchronizationContext** — определяет, на каком потоке продолжится выполнение после await (UI/SynchronizationContext vs Default/ThreadPool).
- **ConfigureAwait(false)** — не возвращаться на исходный контекст синхронизации. Важно для библиотечного кода (избежать дедлоков).

## Task Parallel Library (TPL)
- **Task** — задача без возвращаемого значения (void-аналог в async-мире).
- **Task\<TResult\>** — задача, возвращающая значение типа TResult.
- **ValueTask<T>** — структура, оптимизация для случаев, когда результат может быть доступен синхронно (без аллокации).
- **Task.Run** — запуск делегата на пуле потоков.
- **TaskCompletionSource<T>** — ручное управление завершением Task.
- **Паттерны**: WhenAll, WhenAny, ContinueWith, Task.Factory.StartNew (с осторожностью).

## Parallel
- **Parallel.For / Parallel.ForEach** — параллельное выполнение итераций (разбивает на chunks).
- **Parallel.Invoke** — параллельный запуск нескольких действий.
- **Parallel LINQ (PLINQ)** — `.AsParallel()` для параллельной обработки коллекций.
- **Степень параллелизма**: `ParallelOptions.MaxDegreeOfParallelism`.

## Channels
- **System.Threading.Tasks.Channels** (~.NET Core 3.0) — producer/consumer очередь с async поддержкой.
- **Channel<T>**:
  - `Channel.CreateBounded<T>(capacity)` — с ограничением размера (backpressure).
  - `Channel.CreateUnbounded<T>()` — без ограничений.
  - `WriteAsync` / `ReadAsync` / `TryWrite` / `TryRead`.
  - Поддерживает `IAsyncEnumerable<T>` через `Reader.ReadAllAsync()`.
- Используется для потоковой обработки данных, пайплайнов.

## Dataflow (System.Threading.Tasks.Dataflow)
- **Библиотека Dataflow** — построение конвейеров для асинхронной обработки с буферизацией.
- Основные блоки:
  - `BufferBlock<T>` — хранилище сообщений.
  - `TransformBlock<TInput, TOutput>` — преобразование.
  - `ActionBlock<T>` — выполнение действия.
  - `BroadcastBlock<T>` — рассылка всем подписчикам.
  - `JoinBlock<T1, T2>` — ожидание нескольких источников.
- **DataflowLinkOptions** — PropagateCompletion (автопроброс завершения).

## IAsyncEnumerable<T>
- Асинхронный аналог IEnumerable<T> (C# 8.0).
- Позволяет возвращать элементы по мере их поступления с await:
  ```csharp
  await foreach (var item in GetAsyncSequence())
  ```
- Используется для потоковой передачи данных (gRPC streaming, чтение больших файлов, Kafka consumer).

## CancellationToken
- Механизм отмены async-операций.
- `CancellationTokenSource` — источник, `.Cancel()`.
- `CancellationToken` — передаётся методам, проверяют `.IsCancellationRequested` или бросают `.ThrowIfCancellationRequested()`.
- При отмене — `OperationCanceledException` (TaskCanceledException).

## Важно для интервью
- Разница между CPU-bound (Task.Run, Parallel) и I/O-bound (async/await).
- Async void — только для event-handlers (не обрабатывается вызывающим кодом, исключения роняют процесс).
- Дедлоки: блокировка async метода через `.Result` / `.Wait()` в UI-контексте.
- SynchronizationContext vs ConfigureAwait(false).
- AsyncLocal<T> — аналог ThreadLocal для async-контекста.
