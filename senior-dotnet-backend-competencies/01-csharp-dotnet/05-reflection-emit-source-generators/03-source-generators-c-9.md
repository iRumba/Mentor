## Source Generators (C# 9+)
- Генерация кода на этапе компиляции (компилятор запускает генератор).
- Реализуются как `ISourceGenerator` (или `IIncrementalGenerator`).
- Получают доступ к синтаксическому дереву (Roslyn SyntaxTree) и семантической модели.
- **Преимущества перед Reflection/Emit**:
  - Код генерируется во время компиляции — виден в сборке.
  - Работает с Native AOT (нет reflection).
  - Производительность — нет накладных расходов времени выполнения.
- Примеры: JSON сериализация (System.Text.Json source gen), Regex source gen (C# 11), зависимые от фреймворка (MVVM Community Toolkit, MediatR source gen).
- **IIncrementalGenerator** (C# 9+) — кеширование, быстрая инкрементальная перекомпиляция.
