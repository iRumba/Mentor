## Zero-copy
- Подход — избегать копирования данных.
- Примеры:
  - `Span<T>`/`Memory<T>` для срезов строк/массивов без `Substring`/`CopyTo`.
  - `MemoryPool<T>` и `ArrayPool<T>` — переиспользование буферов.
  - `Utf8JsonReader`, `Utf8Parser` — чтение прямо из UTF-8 байтов без декодирования в string.
  - Stream pipe-lining с `PipeReader`/`PipeWriter`.
- **SequenceReader\<T\>** / **SequencePosition** — работа с последовательностями ReadOnlySequence\<T\> (например, System.IO.Pipelines).
