## Code Style
- **EditorConfig** — `.editorconfig` в корне решения. Параметры: indent_size, end_of_line, charset.
- **Настройки Visual Studio / Rider** — `File | New | File | Code Style` — единый стиль для команды.
- `dotnet format` — CLI-утилита для применения code style (проверка и исправление).
- Convention: команда договаривается о стиле, EditorConfig + dotnet format enforce.
