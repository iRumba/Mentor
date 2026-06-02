## Performance
- **NoTracking** — `AsNoTracking()` отключает отслеживание сущностей. Намного быстрее для чтения.
- **Split Queries** — `AsSplitQuery()` для избежания Cartesian explosion при Include.
- **Compiled Queries** — `EF.CompileQuery()` — компиляция запроса один раз, переиспользование.
- **Batching** — несколько INSERT/UPDATE в один SQL-запрос.
- **Explicit loading** — `Entry().Collection().Load()` — загрузка по требованию.
