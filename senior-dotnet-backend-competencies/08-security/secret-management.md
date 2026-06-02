# Secret Management

## Что такое Secret Management
- Хранение и управление чувствительными данными: API-ключи, пароли БД, сертификаты.
- Не хранить в коде, конфигурационных файлах (особенно в git).
- Использовать специализированные хранилища.

## Azure Key Vault
- Облачное хранилище секретов, ключей шифрования, сертификатов.
- `Azure.Identity` + `SecretClient` — получение секретов через Managed Identity.
- `AddAzureKeyVault()` — интеграция с Configuration API ASP.NET Core.
- Soft delete / Purge protection — восстановление случайно удалённых секретов.
- Access policies / RBAC — разграничение доступа.

## HashiCorp Vault
- Self-hosted или HCP Vault (cloud). Поддержка множества **secret engines**.
- **KV (Key-Value)** — статические секреты.
- **Dynamic secrets** — временные учётные данные (БД, AWS, Azure).
- **Transit** — encryption-as-a-service (шифрование/дешифрование).
- **Cubbyhole** — одноразовые секреты для bootstrap'а.

## Best Practices
- **Rotation** — регулярная смена секретов. В Vault — dynamic secrets (авто-смена).
- **Least privilege** — только те секреты, которые нужны.
- Audit logging — фиксация доступа к секретам.
- Не логировать секреты (сериализация запросов, логи, exception stack trace).

## Важно для интервью
- Azure Key Vault vs HashiCorp Vault — managed vs self-hosted, dynamic secrets.
- Managed Identity (Azure) — лучший способ доступа без паролей.
- .NET User Secrets — только для разработки.
- Git-ignored config files + environment variables — минимальный уровень.
