## Contravariance (контравариантность)
- Позволяет использовать базовый тип там, где ожидается производный.
- Обозначается `in`: `interface IComparer<in T>`.
- **in T** — T может быть только во входных параметрах (in position).
- Пример: `IComparer<Animal>` можно присвоить `IComparer<Dog>`.
