## Code Analysis в CI/CD
- `dotnet build --warningsaserrors` — предупреждения как ошибки.
- `SonarQube` / `SonarCloud` — статический анализ с quality gate.
- Правило: severity для анализаторов — Warning (не Error, чтобы не блокировать сборку при сомнительном правиле).
