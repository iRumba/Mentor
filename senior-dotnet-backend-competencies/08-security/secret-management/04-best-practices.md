## Best Practices
- **Rotation** — регулярная смена секретов. В Vault — dynamic secrets (авто-смена).
- **Least privilege** — только те секреты, которые нужны.
- Audit logging — фиксация доступа к секретам.
- Не логировать секреты (сериализация запросов, логи, exception stack trace).
