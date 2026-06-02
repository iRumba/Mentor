# Generics, Covariance/Contravariance, Constraints

## Generics
- Параметризованные типы — позволяют писать код без привязки к конкретному типу.
- Поддерживают классы, интерфейсы, методы, делегаты.
- **Type safety** на этапе компиляции — избегаем боксинга и приведений.
- **Реализация**: для reference types — специализация одна (размер ссылки одинаковый), для value types — своя специализация под каждый тип (оптимизация).

## Constraints (ограничения)
- `where T : class` — только ссылочные типы.
- `where T : struct` — только значимые типы (включая Nullable).
- `where T : notnull` — не-null типы (C# 8+).
- `where T : new()` — должен иметь конструктор без параметров.
- `where T : BaseClass` — наследование от BaseClass.
- `where T : IInterface` — реализация интерфейса.
- `where T : U` — T должен быть или наследовать U.
- `where T : unmanaged` — неуправляемые типы (C# 7.3+).
- `where T : Enum` / `where T : Delegate` (C# 7.3+).

## Covariance (ковариантность)
- Позволяет использовать производный тип там, где ожидается базовый.
- Обозначается `out`: `interface IEnumerable<out T>`.
- **out T** — T может быть только в возвращаемых значениях (out position).
- Пример: `IEnumerable<Dog>` можно присвоить `IEnumerable<Animal>` (если Dog : Animal).

## Contravariance (контравариантность)
- Позволяет использовать базовый тип там, где ожидается производный.
- Обозначается `in`: `interface IComparer<in T>`.
- **in T** — T может быть только во входных параметрах (in position).
- Пример: `IComparer<Animal>` можно присвоить `IComparer<Dog>`.

## Invariance (инвариантность)
- По умолчанию generics инвариантны — `List<Dog>` не является `List<Animal>`.

## Важно для интервью
- GC-специализация generics для value types vs reference types (Dictionary<int, string> vs Dictionary<string, string>).
- Covariance и contravariance работают **только** с reference types (value types нарушают variance).
- Массивы в C# **ковариантны** (хотя и проблематично): `string[]` → `object[]` (но это нарушает type safety на этапе выполнения).
- Разница между `IEnumerable<T>` (out) и `IList<T>` (no variance).
- Типичная задача: конвертация `IEnumerable<Dog>` в `IEnumerable<Animal>` — возможно (covariance), а `IComparer<Animal>` в `IComparer<Dog>` — тоже возможно (contravariance).
