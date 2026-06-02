# Structured Logging (Serilog)

## Что такое Structured Logging
- Логи не строки, а структурированные записи (JSON) с именованными полями.
- Возможность фильтровать и агрегировать по полям, а не по тексту.
- Поддержка семантики: `Log.Information("User {UserId} logged in", userId)`.

## Serilog
- Основная библиотека для .NET. Конфигурация через JSON или код.
- **Sinks** — куда пишутся логи: Console, File, Seq, Elasticsearch, Azure.
- **Enrichers** — обогащают логи доп. данными (MachineName, ThreadId, Environment).
- **Serilog.AspNetCore** — интеграция с ASP.NET Core pipeline.

## Уровни логирования
- **Verbose** — отладка (всё подряд).
- **Debug** — диагностика разработчика.
- **Information** — бизнес-события (OrderCreated).
- **Warning** — потенциальная проблема.
- **Error** — исключение (500, DB error).
- **Fatal** — крах приложения.

## Best Practices
- Не логать персональные данные (PII).
- Использовать Serilog.Formatting.Compact — компактный JSON.
- `Destructure` — как сериализовать сложные объекты.
- Фильтр по namespace: `MinimumLevel.Override("Microsoft", LogEventLevel.Warning)`.
