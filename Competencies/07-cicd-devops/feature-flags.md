# Feature Flags

## Что такое Feature Flags
- Переключение функциональности без деплоя (триггер в рантайме).
- Позволяет: A/B тестирование, Canary release, Kill switch.
- Ветвление: `if (featureFlags.IsEnabled("NewCheckout")) { ... }`.

## LaunchDarkly
- Облачная платформа feature management.
- Targeting — по userId, email, план подписки, случайный процент и т.д.
- **SDK для .NET** — `ILdClient` (Server-Side, Client-Side).
- Streaming updates — изменения доставляются мгновенно без перезапуска.

## Unleash
- Open-source аналог (с платными расширениями).
- Можно хостить самостоятельно.
- Активация по стратегиям (default, gradual rollout, group-based, custom).

## Best Practices
- Feature flags добавляются и удаляются — технический долг (dead code).
- **Flag retirement** — после полного rollout удалить условие и флаг.
- Тестировать обе ветки флага.
- Избегать nested flags — сложно тестировать.

## Важно для интервью
- Feature flags != configuration (разный lifecycle).
- Время жизни: Short-lived (для rollout) vs Long-lived (релизные переключатели).
- Безопасность: флаги не должны контролировать авторизацию.
- Monitoring — метрики по включённым флагам для отслеживания влияния.
