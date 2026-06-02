## Expression Trees
- Представление кода в виде данных (дерева выражений).
- `System.Linq.Expressions` — `Expression<TDelegate>`.
- Может быть скомпилирован в делегат (`.Compile()`) или проанализирован (Queryable LINQ — EF Core, NHibernate).
- **Виды**: BinaryExpression, MethodCallExpression, ParameterExpression, LambdaExpression, MemberExpression, ConstantExpression и т.д.
- **Используется**: EF Core (перевод LINQ в SQL), AutoMapper (маппинг выражений), валидация, динамические запросы.
- **Expression vs Func**: Expression можно проанализировать (разобрать дерево), Func — только выполнить.
