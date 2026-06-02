## Records (C# 9+)
- Reference type (`record class`) с value equality.
- **Value equality**: два record считаются равными, если все их свойства равны.
- **with-выражения**: `var updated = original with { Name = "new" }` (неразрушающее обновление, иммутабельность).
- **Деструктуризация**: `var (name, age) = person;` (если определён Deconstruct).
- **Позиционные записи**: `record Person(string Name, int Age)` — автоматически генерирует конструктор, свойства, Deconstruct, PrintMembers.
- **record struct** (C# 10) — value type, value equality.
- **readonly record struct** (C# 10) — иммутабельная struct record.
- **ToString()** переопределяется автоматически (выводит все свойства).
- **IEquatable\<T\>** реализуется автоматически.
- **Примечание**: `record` — это `class` с дополнительным синтаксическим сахаром (можно наследоваться).

### Record vs Class
| Характеристика | record | class |
|---|---|---|
| Equality | Value (по свойствам) | Reference (по ссылке) |
| Иммутабельность | По умолчанию `init`-свойства | Обычно get/set |
| Деструктуризация | Встроена | Нужен Deconstruct |
| with-выражения | Да | Нет |
| Наследование | Да (record от record) | Да |
