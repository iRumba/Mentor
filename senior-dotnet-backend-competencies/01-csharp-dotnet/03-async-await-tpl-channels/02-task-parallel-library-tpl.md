## Task Parallel Library (TPL)
- **Task** — задача без возвращаемого значения (void-аналог в async-мире).
- **Task\<TResult\>** — задача, возвращающая значение типа TResult.
- **ValueTask<T>** — структура, оптимизация для случаев, когда результат может быть доступен синхронно (без аллокации).
- **Task.Run** — запуск делегата на пуле потоков.
- **TaskCompletionSource<T>** — ручное управление завершением Task.
- **Паттерны**: WhenAll, WhenAny, ContinueWith, Task.Factory.StartNew (с осторожностью).
