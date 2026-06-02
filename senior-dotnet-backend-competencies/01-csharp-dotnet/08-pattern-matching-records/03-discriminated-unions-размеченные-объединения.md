## Discriminated Unions (размеченные объединения)
- В C# нет встроенной поддержки как в F# (но ожидается).
- Эмуляция через **OneOf** библиотеку или **пользовательские типы** с pattern matching.
- **Базовый подход**: абстрактный тип + иерархия sealed типов + switch/pattern matching:
  ```csharp
  abstract record Result<T>;
  sealed record Success<T>(T Value) : Result<T>;
  sealed record Error<T>(string Message) : Result<T>;
  ```
- Pattern matching по discriminated union вынуждает обработать все варианты (compiler не проверяет полноту, в отличие от F#).
- **OneOf** (библиотека) — `OneOf<T1, T2, T3>` с методом `.Switch()` / `.Match()`.
