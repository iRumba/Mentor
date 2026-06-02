## Dataflow (System.Threading.Tasks.Dataflow)
- **Библиотека Dataflow** — построение конвейеров для асинхронной обработки с буферизацией.
- Основные блоки:
  - `BufferBlock<T>` — хранилище сообщений.
  - `TransformBlock<TInput, TOutput>` — преобразование.
  - `ActionBlock<T>` — выполнение действия.
  - `BroadcastBlock<T>` — рассылка всем подписчикам.
  - `JoinBlock<T1, T2>` — ожидание нескольких источников.
- **DataflowLinkOptions** — PropagateCompletion (автопроброс завершения).
