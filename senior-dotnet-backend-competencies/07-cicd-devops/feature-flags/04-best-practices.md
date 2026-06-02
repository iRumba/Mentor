## Best Practices
- Feature flags добавляются и удаляются — технический долг (dead code).
- **Flag retirement** — после полного rollout удалить условие и флаг.
- Тестировать обе ветки флага.
- Избегать nested flags — сложно тестировать.
