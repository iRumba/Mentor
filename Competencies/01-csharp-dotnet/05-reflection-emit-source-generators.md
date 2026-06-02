# Reflection, Emit, Source Generators, Expression Trees

## Reflection
- Получение информации о типах, сборках, методах, свойствах во время выполнения.
- **Assembly** — загрузка/исследование сборок.
- **Type** — получение метаданных типа: свойства, методы, поля, атрибуты.
- **Activator.CreateInstance** — создание экземпляра по типу (медленно).
- **PropertyInfo / MethodInfo** — чтение/запись свойств, вызов методов через `.GetValue()` / `.SetValue()` / `.Invoke()`.
- **Атрибуты** — получение кастомных атрибутов через `GetCustomAttribute`.
- **Минусы**: медленно (binding, проверки), нет type safety, трудно дебажить, не работает с AOT.

## Emit (System.Reflection.Emit)
- Генерация IL-кода на лету.
- **AssemblyBuilder, ModuleBuilder, TypeBuilder, MethodBuilder, ILGenerator**.
- Используется в ORM (EF Core), DI-контейнерах, AOP-фреймворках (Castle DynamicProxy).
- **DynamicMethod** — упрощённый Emit для методов (без сборки).
- **OpCodes** — IL-инструкции (ldarg, call, ret, newobj и т.д.).
- **Плюсы**: максимальная производительность, почти как рукописный код.
- **Минусы**: сложно, нет type safety, риск невалидного IL.

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

## Expression Trees
- Представление кода в виде данных (дерева выражений).
- `System.Linq.Expressions` — `Expression<TDelegate>`.
- Может быть скомпилирован в делегат (`.Compile()`) или проанализирован (Queryable LINQ — EF Core, NHibernate).
- **Виды**: BinaryExpression, MethodCallExpression, ParameterExpression, LambdaExpression, MemberExpression, ConstantExpression и т.д.
- **Используется**: EF Core (перевод LINQ в SQL), AutoMapper (маппинг выражений), валидация, динамические запросы.
- **Expression vs Func**: Expression можно проанализировать (разобрать дерево), Func — только выполнить.

## Важно для интервью
- Когда использовать Reflection vs Source Generators vs Emit.
- Source generators — предпочтительный путь для .NET 6+ проектов.
- Expression Trees: разница между `IQueryable` (Expression) и `IEnumerable` (Func)?
- Как source generators работают в контексте Native AOT?
- Ограничения Expression Trees: не все конструкции C# поддерживаются (например, async/await, tuple equality).
