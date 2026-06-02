# Автоматизация тестов: SpecFlow / Reqnroll

## Что такое SpecFlow / Reqnroll
- Инструменты **BDD (Behavior-Driven Development)** — тесты на естественном языке (Gherkin).
- **SpecFlow** — популярный BDD-фреймворк для .NET.
- **Reqnroll** — форк SpecFlow (с открытой лицензией, активное развитие).

## Gherkin-синтаксис
- `Feature` — описание функциональности.
- `Scenario` — конкретный пример.
- `Given` — предусловие ("дано").
- `When` — действие ("когда").
- `Then` — проверка ("тогда").
- `Background` — общий контекст для всех сценариев.
- `Scenario Outline` + `Examples` — data-driven сценарии.

## Step definitions
- C#-методы с атрибутами `[Given]`, `[When]`, `[Then]`.
- Регулярные выражения или атрибуты с параметрами для маппинга Gherkin → код.
- `ScenarioContext` — shared context между шагами.

## Важно для интервью
- BDD — общий язык продукта, тестировщиков и разработчиков.
- SpecFlow/Reqnroll — автоматизация acceptance criteria.
- Не заменяет unit/integration тесты — другой уровень.
- Reqnroll — бесплатный open-source форк, SpecFlow — под Tricentis (есть коммерческие ограничения).
