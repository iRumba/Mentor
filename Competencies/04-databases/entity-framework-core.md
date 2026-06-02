# Entity Framework Core

## Основное
- ORM (Object-Relational Mapper) для .NET. Работа с БД через .NET-объекты.
- Поддержка SQL Server, PostgreSQL, SQLite, Cosmos DB, InMemory (тесты).

## Performance
- **NoTracking** — `AsNoTracking()` отключает отслеживание сущностей. Намного быстрее для чтения.
- **Split Queries** — `AsSplitQuery()` для избежания Cartesian explosion при Include.
- **Compiled Queries** — `EF.CompileQuery()` — компиляция запроса один раз, переиспользование.
- **Batching** — несколько INSERT/UPDATE в один SQL-запрос.
- **Explicit loading** — `Entry().Collection().Load()` — загрузка по требованию.

## Проблемы
- **N+1 query** — ленивая загрузка в цикле. Решение: `Include` / `ThenInclude`.
- **Cartesian explosion** — множество Include → экспоненциальный рост строк.
- **Auto-migration** — в проде опасно, лучше миграции через `dotnet ef migrations script`.

## Raw SQL
- `FromSqlRaw()` / `FromSqlInterpolated()` — прямой SQL для сложных запросов.
- `ExecuteSqlRaw()` / `ExecuteSqlInterpolated()` — для модификации.

## Важно для интервью
- EF Core vs EF6 — отличия (EF Core — кроссплатформенный, lightweight, без EDMX).
- Когда EF Core, когда Dapper — tradeoff между speed и productivity.
- DbContext lifetime — Scoped (один на запрос).
- Migration strategy в production.
