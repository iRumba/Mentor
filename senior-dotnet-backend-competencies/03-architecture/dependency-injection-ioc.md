# Dependency Injection, IoC-контейнеры

## Inversion of Control (IoC)
- Общий принцип: управление потоком программы передаётся внешнему фреймворку/контейнеру.
- **Dependency Injection** — конкретная реализация IoC: зависимости передаются объекту извне.

## IoC-контейнеры сторонние
- **Autofac** — мощный контейнер с поддержкой декораторов, перехватчиков (AOP), модулей.
- **Scrutor** — расширение для встроенного DI: `Scan()` для сборки регистраций, декораторы.
- Другие: Castle Windsor, SimpleInjector, StructureMap (устарел).

## Продвинутые возможности
- **Декоратор** — обёртка вокруг сервиса, добавляющая сквозную функциональность (логирование, кэш).
- **Перехватчик (Interception)** — AOP через Castle DynamicProxy / Autofac.
- **Keyed services** — множественные реализации, выбор по ключу.
- **Module scanning** — авто-регистрация по типу/имени.

## Важно для интервью
- Почему Autofac/Scrutor, если есть встроенный DI? (Авто-регистрация, декораторы, AOP, lifetime events).
- Captive dependency — популярная проблема.
- `IPostSharp` vs Castle DynamicProxy — compile-time vs runtime AOP.
- Как тестировать DI-конфигурацию — `ValidateOnStart`, integration tests.
