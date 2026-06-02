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
