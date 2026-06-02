# Code Style, Analyzers, Roslyn

## Code Style
- **EditorConfig** — `.editorconfig` в корне решения. Параметры: indent_size, end_of_line, charset.
- **Настройки Visual Studio / Rider** — `File | New | File | Code Style` — единый стиль для команды.
- `dotnet format` — CLI-утилита для применения code style (проверка и исправление).
- Convention: команда договаривается о стиле, EditorConfig + dotnet format enforce.

## Roslyn Analyzers
- **Roslyn** — компиляторная платформа (.NET Compiler Platform).
- **Analyzers** — плагины к компилятору, проверяющие код в реальном времени (IDE, build time).
- Встроенные: `CA1062` (null check), `CA1000` (naming).
- **IDExxxx** — IDE-подсказки (code style).
- **FxCopAnalyzers / Microsoft.CodeAnalysis.NetAnalyzers** — анализ безопасности и производительности.

## Популярные анализаторы
- **SonarAnalyzer** — правила SonarQube для .NET.
- **StyleCop.Analyzers** — проверка code style и naming conventions.
- **Roslynator** — 1900+ правил и рефакторингов.
- **SerilogAnalyzer** — правила для Serilog (местозаполнители, уровни).

## Code Analysis в CI/CD
- `dotnet build --warningsaserrors` — предупреждения как ошибки.
- `SonarQube` / `SonarCloud` — статический анализ с quality gate.
- Правило: severity для анализаторов — Warning (не Error, чтобы не блокировать сборку при сомнительном правиле).

## Важно для интервью
- EditorConfig — обязателен в проекте с командой.
- Линтеры и анализаторы — это автоматический code review.
- Roslyn — это не только анализаторы, но и code fixes, refactorings.
- Можно писать кастомные анализаторы (для бизнес-правил).
