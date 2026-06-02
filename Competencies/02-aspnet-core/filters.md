# Filters

## Что такое фильтры
- Атрибуты или классы, выполняющиеся на определённых этапах pipeline MVC.
- Позволяют внедрить сквозную логику без дублирования.

## Типы фильтров (порядок выполнения)
1. **Authorization Filter** (`IAsyncAuthorizationFilter`) — выполняется первым, до контроллера. Проверка прав доступа.
2. **Resource Filter** (`IAsyncResourceFilter`) — оборачивает всю модель (контроллер + action + фильтры). Подходит для кэширования.
3. **Action Filter** (`IAsyncActionFilter`) — до и после выполнения action.
4. **Exception Filter** (`IAsyncExceptionFilter`) — обрабатывает необработанные исключения из action.
5. **Result Filter** (`IAsyncResultFilter`) — до и после выполнения result (до рендеринга).

## Порядок выполнения
- Вход: Auth → Resource → Action → Result → Exception (если ошибка).
- Выход: Result → Action → Resource.

## Factory filters
- `IFilterFactory` — создаёт экземпляр фильтра по запросу, поддерживает Dependency Injection.

## Важно для интервью
- Filter vs Middleware: фильтры работают только в контексте MVC/Minimal API, middleware — глобально.
- `IAsync*` vs синхронные версии — предпочитать async.
- Order фильтров — через свойство `Order` (меньше = раньше).
- `IExceptionFilter` ловит только исключения из action, не из middleware.
