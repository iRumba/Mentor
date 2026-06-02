## Azure Key Vault
- Облачное хранилище секретов, ключей шифрования, сертификатов.
- `Azure.Identity` + `SecretClient` — получение секретов через Managed Identity.
- `AddAzureKeyVault()` — интеграция с Configuration API ASP.NET Core.
- Soft delete / Purge protection — восстановление случайно удалённых секретов.
- Access policies / RBAC — разграничение доступа.
