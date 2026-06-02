# PostConfigure и Валидация Опций

Иногда недостаточно просто привязать JSON к классу. Требуются вычисляемые значения, сложные зависимости между полями или строгая проверка корректности данных перед запуском приложения.

## PostConfigure

`PostConfigure<T>` используется для окончательной настройки параметров. Он выполняется **после** всех вызовов `Configure<T>`.

**Зачем это нужно?**
1. **Значения по умолчанию:** Если какая-то настройка не была указана в JSON, в `PostConfigure` можно задать разумный дефолт.
2. **Вычисляемые поля:** Если одно поле зависит от другого (например, `FullUrl = BaseUrl + "/api"`).
3. **Интеграция с другими сервисами:** Когда настройки зависят от данных, которые доступны только в DI.

```csharp
services.PostConfigure<MySettings>(options => {
    if (string.IsNullOrEmpty(options.CacheKey)) {
        options.CacheKey = "Default_Cache_Key_" + DateTime.Now.Year;
    }
});
```

## Валидация настроек

Ошибка в конфигурации (например, опечатка в URL базы данных) может привести к падению приложения в случайный момент. Лучший подход — **Fail Fast** (падение при старте).

### 1. DataAnnotations
Вы можете использовать стандартные атрибуты валидации (`[Required]`, `[Range]`, `[EmailAddress]`) в классах опций.

```csharp
public class DatabaseOptions {
    [Required, MinLength(5)]
    public string ConnectionString { get; set; }

    [Range(1, 100)]
    public int MaxPoolSize { get; set; }
}
```

Чтобы эта валидация работала, нужно включить её при регистрации:
```csharp
builder.Services.AddOptions<DatabaseOptions>()
    .Bind(builder.Configuration.GetSection("Database"))
    .ValidateDataAnnotations() 
    .ValidateOnStart(); // Приложение упадет при запуске, если данные неверны
```

### 2. Custom Validation (IValidateOptions\<T\>)
Для сложной логики (например, проверка, что `Min` всегда меньше `Max`) создается отдельный класс валидатор.

```csharp
public class MySettingsValidator : IValidateOptions<MySettings> {
    public ValidateOptionsResult Validate(string name, MySettings options) {
        if (options.MinTimeout > options.MaxTimeout) {
            return ValidateOptionsResult.Fail("MinTimeout cannot be greater than MaxTimeout");
        }
        return ValidateOptionsResult.Success;
    }
}
// Регистрация: services.AddSingleton<IValidateOptions<MySettings>, MySettings laValidator>();
```

## Сравнение Configure vs PostConfigure

| Метод | Когда выполняется | Цель | Типичный сценарий |
| :--- | :--- | :--- | :--- |
| `Configure` | Сначала | Привязка JSON $\rightarrow$ POCO | Маппинг базовых настроек из файла |
| `PostConfigure` | В конце | Доводка / Корректировка | Задание дефолтов, расчет производных полей |
