## Best Practices
- Не логать персональные данные (PII).
- Использовать Serilog.Formatting.Compact — компактный JSON.
- `Destructure` — как сериализовать сложные объекты.
- Фильтр по namespace: `MinimumLevel.Override("Microsoft", LogEventLevel.Warning)`.
