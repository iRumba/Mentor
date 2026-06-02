## Что такое Feature Flags
- Переключение функциональности без деплоя (триггер в рантайме).
- Позволяет: A/B тестирование, Canary release, Kill switch.
- Ветвление: `if (featureFlags.IsEnabled("NewCheckout")) { ... }`.
