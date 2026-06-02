# Реляционные БД: SQL Server, PostgreSQL

## Индексы
- **Clustered** — физический порядок данных (один на таблицу). SQL Server — по PK по умолчанию.
- **Non-clustered** — отдельная структура с указателем на данные.
- **Covering index** — включает все поля запроса, не обращается к таблице.
- **Filtered / Partial index** — только часть строк (для частых запросов).

## Планы запросов
- **Execution plan** — как оптимизатор решил выполнить запрос.
- Scan (Seq Scan) vs Seek (Index Seek) — что предпочтительнее.
- Lookup (Key/RID Lookup) — признак, что индекс не покрывает запрос.

## Оконные функции
- `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()` — нумерация строк в окне.
- `LEAD()`, `LAG()` — доступ к соседним строкам.
- `SUM() OVER (PARTITION BY ...)` — агрегаты без группировки.

## CTE (Common Table Expressions)
- `WITH ... AS (...)` — временный именованный результат.
- Рекурсивные CTE — для иерархий (деревья, графы).

## Важно для интервью
- Explain plan (PostgreSQL) / Actual execution plan (SQL Server) — чтение планов.
- Индекс vs table scan — когда один выгоднее другого (селективность).
- `NOLOCK` / `READ UNCOMMITTED` — dirty reads, когда допустимо.
- Отличия SQL Server от PostgreSQL: типы данных, схемы, MVCC, vacuum.
