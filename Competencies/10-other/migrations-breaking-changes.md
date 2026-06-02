# Миграции и Breaking Changes

## Миграции кода
- Переход на новую версию .NET (net6 → net8 → net10).
- **Breaking changes** — incompatible changes в платформе (API removed, behaviour changed).
- `dotnet try-convert` / `upgrade-assistant` — утилиты для автоматизации.
- Проверка через `dotnet build` + `dotnet publicapi` (наличие/отсутствие API).

## Миграции БД
- **EF Core Migrations** — `dotnet ef migrations add`, `database update`.
- **Reverse engineering / Scaffold** — `dotnet ef dbcontext scaffold`.
- **SQL Server → PostgreSQL** — осторожно: типы, функции, схемы.
- **Основной принцип**: backward-compatible (без downtime).
  - Expand (добавить новое) → Migrate (перенести данные) → Contract (удалить старое).

## Breaking Changes API
- В API publish'ить новую версию (v1, v2), не ломать старую.
- **Additive changes** — безопасны (новое поле, новый endpoint).
- **Subtractive changes** — breaking (удаление поля, изменение типа).
- Semantic versioning — MAJOR for breaking changes.

## Процесс
1. Анализ зависимостей (пакеты, API, БД).
2. Тестирование на staging (интеграционные тесты).
3. Rolling upgrade (постепенно, инстанс за инстансом).
4. Monitoring после миграции.

## Важно для интервью
- Breaking changes неизбежны — главное управлять ими.
- `.runtimeconfig.json` — target framework.
- `dotnet --list-sdks` — установленные SDK.
- Feature Detection Pattern — проверять наличие API в рантайме (для библиотек).
