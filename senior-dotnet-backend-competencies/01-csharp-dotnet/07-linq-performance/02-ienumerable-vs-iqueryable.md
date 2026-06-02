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
