## unsafe code
- Блоки `unsafe` — прямой доступ к указателям, адресной арифметике.
- **fixed** — фиксация управляемой памяти (pinning), чтобы GC не перемещал объект:
  ```csharp
  fixed (int* ptr = &array[0])
  ```
- **stackalloc** — выделение памяти на стеке (быстро, но ограничено):
  ```csharp
  Span<byte> buffer = stackalloc byte[256];
  ```
- Используется: криптография, парсеры, high-performance вычисления, interop.
