# Dependency Injection (DI)

## Регистрация сервисов
- `AddSingleton<T>` — один экземпляр на всё приложение.
- `AddScoped<T>` — один экземпляр на каждый HTTP-запрос.
- `AddTransient<T>` — новый экземпляр при каждом запросе DI-контейнера.
- `AddKeyedSingleton/Scoped/Transient` (.NET 8+) — регистрация по ключу.

## Встроенный контейнер
- `Microsoft.Extensions.DependencyInjection` — встроенный DI в ASP.NET Core.
- Поддерживает конструкторную инъекцию, внедрение через параметры методов (для Minimal API).
- Контейнер сам управляет временем жизни и освобождением `IDisposable`.

## Scope
- `IServiceScope` — создаёт дочерний контейнер с изолированными Scoped-сервисами.
- Используется в фоновых задачах (`IHostedService`) для получения Scoped-сервисов.

## Важно для интервью
- Captive dependency — регистрация Scoped как Singleton (живёт дольше, чем задумано).
- Scope validation в `WebApplicationBuilder` — проверяет, что Scoped не заинжектирован в Singleton.
- Контейнеры третьих сторон (Autofac, Scrutor, SimpleInjector) — расширяют функциональность (декораторы, перехватчики).
- `TryAdd*` — регистрация только если сервис ещё не зарегистрирован.
