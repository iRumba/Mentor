## GraphQL
- Язык запросов от Facebook. Клиент сам указывает, какие поля нужны.
- **Single endpoint** (`POST /graphql`), вся логика в resolvers.
- Проблемы: N+1, сложное кэширование, авторизация на уровне полей.
- **Batch, DataLoader** — решение N+1 для .NET.
