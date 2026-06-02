## Options pattern
- **IOptions\<T\>** — фиксируется при старте, не обновляется.
- **IOptionsSnapshot\<T\>** — перечитывается при каждом запросе (Scoped).
- **IOptionsMonitor\<T\>** — перечитывается при изменении (Singleton, с поддержкой `OnChange`).
- `services.Configure<T>(section)` — регистрация из конфигурации.
- `services.PostConfigure<T>(action)` — пост-обработка после всех `Configure`.
