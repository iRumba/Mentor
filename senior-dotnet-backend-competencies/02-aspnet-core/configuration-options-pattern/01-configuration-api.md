## Configuration API
- Иерархическая конфигурация из нескольких источников: `appsettings.json`, env vars, secrets, CLI args.
- Последний источник имеет приоритет (последний перезаписывает).
- `IConfiguration` — ключ-значение, доступ через `config["Section:Key"]`.
- `Bind()` — маппинг секции в POCO-класс.
