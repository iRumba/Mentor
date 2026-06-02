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
