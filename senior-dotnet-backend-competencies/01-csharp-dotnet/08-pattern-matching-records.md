# Pattern Matching, Records, Discriminated Unions

## Pattern Matching (сопоставление с шаблоном)
Развивается с C# 7.0. Позволяет компактно проверять типы и значения.

### Основные виды
- **Switch expression** (C# 8+):
  ```csharp
  result = value switch
  {
      int i => $"int {i}",
      string s => $"string {s}",
      null => "null",
      _ => "other"
  };
  ```
- **Type pattern** — `x is int i` (проверка типа + захват переменной).
- **Property pattern** — проверка свойств: `{ Name: "test", Age: > 18 }`.
- **Positional pattern** — деструктуризация: `(int X, int Y) => ...`.
- **List pattern** (C# 11) — `[1, 2, ..]`, `[first, .. middle, last]`.
- **Var pattern** — `var x` (захват в переменную, не проверяет тип).
- **Not pattern** (C# 9) — `not null`, `not 0`.
- **Relational pattern** (C# 9) — `<`, `>`, `<=`, `>=`, `and`, `or`.
- **Constant pattern** — сравнение с константой: `x is 42`, `x is "hello"`.

### Discard (`_`) — wildcard для неиспользуемых значений.

## Records (C# 9+)
- Reference type (`record class`) с value equality.
- **Value equality**: два record считаются равными, если все их свойства равны.
- **with-выражения**: `var updated = original with { Name = "new" }` (неразрушающее обновление, иммутабельность).
- **Деструктуризация**: `var (name, age) = person;` (если определён Deconstruct).
- **Позиционные записи**: `record Person(string Name, int Age)` — автоматически генерирует конструктор, свойства, Deconstruct, PrintMembers.
- **record struct** (C# 10) — value type, value equality.
- **readonly record struct** (C# 10) — иммутабельная struct record.
- **ToString()** переопределяется автоматически (выводит все свойства).
- **IEquatable\<T\>** реализуется автоматически.
- **Примечание**: `record` — это `class` с дополнительным синтаксическим сахаром (можно наследоваться).

### Record vs Class
| Характеристика | record | class |
|---|---|---|
| Equality | Value (по свойствам) | Reference (по ссылке) |
| Иммутабельность | По умолчанию `init`-свойства | Обычно get/set |
| Деструктуризация | Встроена | Нужен Deconstruct |
| with-выражения | Да | Нет |
| Наследование | Да (record от record) | Да |

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

## Важно для интервью
- Разница `record class` vs `record struct` (reference vs value + разное поведение с наследованием).
- Как record реализует Value Equality (сравнивает все поля/свойства рекурсивно через EqualityComparer<T>.Default).
- Init-only setters: `{ get; init; }` — инициализация только в конструкторе или object initializer.
- Pattern matching с `switch` expression — когда лучше обычного if-else?
- Практическое применение: обработка Result<T> (Success/Error/Failure), обработка State машины, парсинг AST.
