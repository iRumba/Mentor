## Структуры (struct)
- Когда использовать: небольшие, иммутабельные, логически единые значения (Point, DateTime, Complex).
- Рекомендации Microsoft: struct должна быть ≤ 16 байт.
- **ref struct** — только на стеке, не может попасть в heap (замыкания, async, boxed). Span<T> — ref struct.
- **readonly struct** — гарантирует иммутабельность, избегает защитного копирования (`in` parameter).
- **record struct** (C# 10) — структурные записи с value equality.
