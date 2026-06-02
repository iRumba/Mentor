# Configuration API, Options pattern, PostConfigure

## Configuration API
- Иерархическая конфигурация из нескольких источников: `appsettings.json`, env vars, secrets, CLI args.
- Последний источник имеет приоритет (последний перезаписывает).
- `IConfiguration` — ключ-значение, доступ через `config["Section:Key"]`.
- `Bind()` — маппинг секции в POCO-класс.

## Options pattern
- **IOptions\<T\>** — фиксируется при старте, не обновляется.
- **IOptionsSnapshot\<T\>** — перечитывается при каждом запросе (Scoped).
- **IOptionsMonitor\<T\>** — перечитывается при изменении (Singleton, с поддержкой `OnChange`).
- `services.Configure<T>(section)` — регистрация из конфигурации.
- `services.PostConfigure<T>(action)` — пост-обработка после всех `Configure`.

## PostConfigure
- `PostConfigure` — изменяет уже зарегистрированные опции (доводка, валидация).
- `ValidateDataAnnotations` / `ValidateOnStart` — валидация при старте.

## Важно для интервью
- Разница между IOptions, IOptionsSnapshot, IOptionsMonitor.
- Secrets Manager в Development-режиме (User Secrets).
- Azure App Configuration / Key Vault как удалённые провайдеры.
- `Configure` vs `PostConfigure` vs `ConfigureAll`.
