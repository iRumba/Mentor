## Emit (System.Reflection.Emit)
- Генерация IL-кода на лету.
- **AssemblyBuilder, ModuleBuilder, TypeBuilder, MethodBuilder, ILGenerator**.
- Используется в ORM (EF Core), DI-контейнерах, AOP-фреймворках (Castle DynamicProxy).
- **DynamicMethod** — упрощённый Emit для методов (без сборки).
- **OpCodes** — IL-инструкции (ldarg, call, ret, newobj и т.д.).
- **Плюсы**: максимальная производительность, почти как рукописный код.
- **Минусы**: сложно, нет type safety, риск невалидного IL.
