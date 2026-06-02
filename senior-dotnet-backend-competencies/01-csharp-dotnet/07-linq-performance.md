# LINQ (Performance, Deferred Execution, IQueryable vs IEnumerable)

## LINQ to Objects

### Deferred Execution (отложенное выполнение)
- LINQ запросы не выполняются при определении — только при переборе (foreach, ToList, Count, First).
- Цепочки методов: `Where(...).Select(...).Take(10)` — фильтрация применяется к каждому элементу поочерёдно, без промежуточных коллекций.
- Проблемы: множественный перебор источника (например, `list.Where(x => x > 5).Count()` — перебирает дважды).

### Performance проблемы
- **Множественная итерация**: вызов `.Count()`, `.Any()`, `.ToList()` на одном и том же запросе перебирает источник заново.
- **Захват в замыкание** — аллокации.
- **Select + Where порядок**: `Where().Select()` vs `Select().Where()` — первый вариант быстрее (меньше объектов проходит трансформацию).
- **OrderBy** — стабильная сортировка O(n log n), создаёт копию данных.
- **GroupBy** — материализует всю группу в памяти (lazy только для ключей).
- **Cast\<T\> / OfType\<T\>** — может быть медленным для больших коллекций.

### Best practices
- `Any()` вместо `Count() > 0` (Count может перебрать весь Enumerable).
- `ToDictionary` / `ToHashSet` / `ToLookup` для частого поиска.
- Для больших данных — ручной foreach с `for` циклом (избежать накладных расходов LINQ).
- Использовать `HashSet<T>` / `Dictionary<TKey, TValue>` для Contains в сложных запросах.

## IEnumerable vs IQueryable

| Характеристика | IEnumerable | IQueryable |
|---|---|---|
| Выполнение | In-memory (LINQ to Objects) | Может быть переведён в SQL/LINQ provider |
| Дерево выражений | Func / делегаты | Expression Trees |
| Фильтрация | На стороне клиента (все данные загружаются) | На стороне сервера (SQL WHERE) |
| Использование | In-memory коллекции (List, Array) | Базы данных (EF Core) |

- **AsEnumerable()** — переключает с IQueryable на IEnumerable (force client-side evaluation). Часто костыль, которого следует избегать.
- EF Core: `IQueryable<T>` строится как Expression Tree, который транслируется в SQL. Материализация приводит к отправке SQL.
- **Грабли**: после `ToList()` все дальнейшие Where/Select — уже Linq-to-Objects (in-memory).

### LINQ Chaining (метод расширения)
```csharp
// IQueryable — всё будет в одном SQL запросе
query.Where(x => x.Age > 18).OrderBy(x => x.Name).Select(x => x.Email);

// IEnumerable — всё в памяти
query.Where(x => x.Age > 18).AsEnumerable().OrderBy(x => x.Name);
```

## Parallel LINQ (PLINQ)
- `.AsParallel()` — параллельная обработка коллекции (разбивает на chunks, обрабатывает на нескольких потоках).
- `.AsOrdered()` — сохранить порядок элементов.
- Подходит для CPU-bound операций.
- **Не** для I/O-bound (блокирует потоки).

## Важно для интервью
- Разница между Immediate Execution (ToList, ToArray, Count, First) и Deferred Execution (Where, Select, SelectMany).
- Почему `.Where(x => expensive(x)).First()` эффективнее `.First(x => expensive(x))`? (в первом случае все пройдут фильтр, во втором — только до первого совпадения).
- Как EF Core переводит LINQ в SQL? (Expression Tree → SQL AST → строка SQL).
- Где LINQ может быть bottleneck? (множественный перебор, N+1 через ORM, преждевременная материализация).
- Использование `IComparer<T>` / `IEqualityComparer<T>` в LINQ операциях.
