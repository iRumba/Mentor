## P/Invoke (Platform Invoke)
- Механизм вызова функций из нативных DLL (WinAPI, C-библиотеки) из управляемого кода.
- **DllImport** — атрибут, описывающий нативную функцию:
  ```csharp
  [DllImport("user32.dll", CharSet = CharSet.Auto)]
  public static extern int MessageBox(IntPtr hWnd, string text, string caption, uint type);
  ```
- **Параметры**:
  - `EntryPoint` — имя функции в DLL (если отличается от C#).
  - `CharSet` — Ansi / Auto / Unicode (кодировка строк).
  - `CallingConvention` — StdCall (WinAPI) / Cdecl (C lib).
  - `SetLastError = true` — можно получить ошибку через `Marshal.GetLastWin32Error()`.
  - `BestFitMapping`, `ThrowOnUnmappableChar` — для строк.
  - `PreserveSig` — true (функция возвращает HRESULT).
- **Маршалинг** — автоматическое преобразование типов между управляемым и неуправляемым кодом:
  - Blittable types (int, long, byte, IntPtr) — копируются напрямую.
  - Non-blittable (string, bool, struct с layout) — маршалинг (копирование + преобразование).
  - `MarshalAs` — точное указание способа маршалинга (например, `[MarshalAs(UnmanagedType.LPStr)]`).

### Маршалинг структур
- **StructLayout** — `LayoutKind.Sequential` (последовательное расположение, как в C) или `LayoutKind.Explicit` (с FieldOffset).
- **Size** — общий размер структуры (для fixed-size buffers).
- **Pack** — выравнивание полей.

### SafeHandle
- Абстрактный класс для безопасной обёртки нативного handle.
- **CriticalHandle** / **SafeHandleZeroOrMinusOneIsInvalid** — для Windows handles.
- Реализует `IDisposable` и финализацию.
- Предотвращает утечки ресурсов.
- Использовать вместо `IntPtr` для надёжности.

### Source Generator для P/Invoke (C# 9+, .NET 7)
- **LibraryImport** (вместо DllImport) — source generation, не использует marshalling engine на runtime.
- **Преимущества**: лучше производительность, AOT-совместимость, меньше накладных расходов.
- `[LibraryImport("user32.dll")]` — аналог DllImport, но генерирует маршалинг на этапе компиляции.
- Пока не поддерживает все сценарии (например, SetLastError, variadic args).
