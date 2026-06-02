# Unit-тесты: xUnit / NUnit, Moq / NSubstitute, FluentAssertions

## xUnit / NUnit
- **xUnit** — современный стандарт для .NET. `[Fact]` (без параметров), `[Theory]` (с параметрами).
- **NUnit** — более традиционный. `[Test]`, `[TestCase]`, `[SetUp]` / `[TearDown]`.
- xUnit — конструктор как Setup, `IDisposable` как Teardown (без атрибутов).
- Оба поддерживают параллельное выполнение тестов.

## Moq / NSubstitute
- **Moq** — самый популярный: `mock.Setup(x => x.Method()).Returns(value)`. `Verify()` для проверок.
- **NSubstitute** — более лаконичный синтаксис: `sub.Method().Returns(value)`, `sub.Received(1).Method()`.
- Mock vs Stub: Mock — проверяет взаимодействие, Stub — подставляет данные.

## FluentAssertions
- Человекочитаемые assertion'ы: `result.Should().Be(expected)`, `list.Should().ContainSingle()`.
- Лучше сообщения об ошибках, чем встроенные assertion'ы.

## Важно для интервью
- Arrange-Act-Assert (AAA) — стандартная структура теста.
- Избегать моки внешних зависимостей в интеграционных тестах (только в unit).
- Fixture setup / teardown — жизненный цикл (collection, class, test).
- AutoFixture / Bogus — генерация тестовых данных.
