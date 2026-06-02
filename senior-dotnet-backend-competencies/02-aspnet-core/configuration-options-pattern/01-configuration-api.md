# Configuration API

Система конфигурации в ASP.NET Core построена на принципе «ключ-значение» и объединяет данные из различных источников в единую иерархическую структуру.

## Источники конфигурации

Конфигурация собирается из одного или нескольких провайдеров. Порядок регистрации провайдеров имеет решающее значение, так как последние добавленные переопределяют предыдущих.

**Типичный порядок (встроенный в `Host.CreateDefaultBuilder`):**
1. `appsettings.json` (основной файл).
2. `appsettings.{Environment}.json` (специфичные для среды настройки).
3. **User Secrets** (только для Development, хранится вне проекта).
4. **Environment Variables** (переменные окружения, часто используются в Docker/K8s).
5. **Command Line Arguments** (аргументы запуска).

**Пример приоритета:** Если в `appsettings.json` указан порт 5000, а в переменной окружения `ASPNETCORE_PORT` — 8080, приложение будет использовать 8080.

## Работа с IConfiguration

Интерфейс `IConfiguration` позволяет получать доступ к данным через строковые ключи.

```csharp
public class MyService(IConfiguration config) 
{
    public void DoWork() 
    {
        // Простой доступ
        var apiKey = config["ApiKey"];
        
        // Доступ к секции (вложенный объект)
        var dbSettings = config.GetSection("DatabaseSettings");
        var connectionString = dbSettings["ConnectionString"];
    }
}
```

## Bind (Маппинг в POCO)

Использование строковых ключей (`config["Key"]`) считается плохой практикой для бизнес-логики (Magic Strings). Правильный подход — маппинг секции на простой C# класс (POCO).

```csharp
public class SmtpOptions {
    public string Server { get; set; }
    public int Port { get; set; }
}

// В коде:
var smtpOptions = new SmtpOptions();
config.GetSection("Smtp").Bind(smtpOptions); 
// Теперь smtpOptions заполнен данными из конфига
```

## Best Practices и Pitfalls

- **Разделение сред:** Используйте `appsettings.Development.json` и `appsettings.Production.json` для разделения настроек.
- **Секреты:** Никогда не храните пароли, API-ключи или токены в JSON файлах, которые попадают в Git. Используйте User Secrets для разработки и Key Vault / Environment Variables для продакшена.
- **Case Insensitivity:** По умолчанию ключи в конфигурации ASP.NET Core не чувствительны к регистру.
