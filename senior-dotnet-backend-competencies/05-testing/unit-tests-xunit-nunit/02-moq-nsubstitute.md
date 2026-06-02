## Moq / NSubstitute
- **Moq** — самый популярный: `mock.Setup(x => x.Method()).Returns(value)`. `Verify()` для проверок.
- **NSubstitute** — более лаконичный синтаксис: `sub.Method().Returns(value)`, `sub.Received(1).Method()`.
- Mock vs Stub: Mock — проверяет взаимодействие, Stub — подставляет данные.
