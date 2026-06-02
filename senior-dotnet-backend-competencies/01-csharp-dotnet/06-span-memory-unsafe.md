# Span\<T\>, Memory\<T\>, unsafe code, zero-copy

## Span\<T\>
- `ref struct` — тип-значение, представляет непрерывную область памяти.
- **ref struct** — живёт только на стеке, не может быть захвачен в heap (не в async, не в field класса, не в замыкания, не в boxing).
- Позволяет работать с разными типами памяти единообразно: массивы, строки, native память, стеки (stackalloc).
- **Срезы без копирования**: `span.Slice(start, length)` — без аллокаций.
- **Методы**: IndexOf, Contains, SequenceEqual, Fill, Clear, ToArray (с копированием).
- Производительность в разы выше массивов для операций с подстроками, парсинга.

## ReadOnlySpan\<T\>
- Неизменяемый вариант Span<T>, часто используется со строками (`AsSpan()`).
- `ReadOnlySpan<char>` — эффективная работа со строками без выделения памяти.

## Memory\<T\>
- Структура (не ref struct), может жить на куче (поля класса, async, замыкания).
- Предоставляет `Span` через `.Span` свойство (актуальный на момент доступа).
- Подходит для API, где Span нельзя использовать (асинхронные методы, классы).
- **IMemoryOwner\<T\>** — пул памяти, возвращаемый `MemoryPool<T>.Shared.Rent()`.

## unsafe code
- Блоки `unsafe` — прямой доступ к указателям, адресной арифметике.
- **fixed** — фиксация управляемой памяти (pinning), чтобы GC не перемещал объект:
  ```csharp
  fixed (int* ptr = &array[0])
  ```
- **stackalloc** — выделение памяти на стеке (быстро, но ограничено):
  ```csharp
  Span<byte> buffer = stackalloc byte[256];
  ```
- Используется: криптография, парсеры, high-performance вычисления, interop.

## Zero-copy
- Подход — избегать копирования данных.
- Примеры:
  - `Span<T>`/`Memory<T>` для срезов строк/массивов без `Substring`/`CopyTo`.
  - `MemoryPool<T>` и `ArrayPool<T>` — переиспользование буферов.
  - `Utf8JsonReader`, `Utf8Parser` — чтение прямо из UTF-8 байтов без декодирования в string.
  - Stream pipe-lining с `PipeReader`/`PipeWriter`.
- **SequenceReader\<T\>** / **SequencePosition** — работа с последовательностями ReadOnlySequence\<T\> (например, System.IO.Pipelines).

## Важно для интервью
- Почему Span<T> — ref struct? (безопасность, GC не может перемещать указатель).
- Когда Span, когда Memory?
- Чем `Substring` отличается от `AsSpan().Slice()`? (Substring — аллокация, Slice — нет).
- `ArrayPool<T>.Shared` — пул массивов для временных буферов.
- Stackalloc vs heap allocation: производительность, ограничения.
- fixed statement — для чего нужен pinning при interop и unsafe.
