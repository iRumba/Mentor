## Covariance (ковариантность)
- Позволяет использовать производный тип там, где ожидается базовый.
- Обозначается `out`: `interface IEnumerable<out T>`.
- **out T** — T может быть только в возвращаемых значениях (out position).
- Пример: `IEnumerable<Dog>` можно присвоить `IEnumerable<Animal>` (если Dog : Animal).
