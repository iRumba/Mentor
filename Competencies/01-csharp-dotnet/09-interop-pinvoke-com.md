# Интероп с нативным кодом (P/Invoke, COM)

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

## COM Interop
- Взаимодействие с COM-объектами (Component Object Model).
- **RCW (Runtime Callable Wrapper)** — управляемая обёртка вокруг COM-объекта.
- **CCW (COM Callable Wrapper)** — обёртка управляемого класса для COM.
- Создание:
  - Через `Type.GetTypeFromProgID("Excel.Application")` + `Activator.CreateInstance`.
  - Через библиотеку типов (TLBIMP — импорт TLB в сборку).
- **Marshal.ReleaseComObject** — освобождение COM-объекта (важно!).
- **Marshal.FinalReleaseComObject** — принудительно уменьшает счётчик ссылок до нуля.
- **COM в .NET Core 5+**: только Windows (Windows-only). В .NET 6+ появилась возможность на Linux (нет).
- **Грабли**: утечки RCW, двухслойное освобождение, STA/MTA apartment model.

## C++/CLI (C++/CLI)
- Промежуточный вариант — использование смешанных сборок (mixed-mode).
- Позволяет вызывать C++ код напрямую, без P/Invoke накладных.
- Часто используется как обёртка над существующими C++ библиотеками.
- **Минусы**: умирающая технология, не поддерживается в Native AOT.

## Важно для интервью
- Blittable vs Non-blittable типы и их влияние на производительность.
- DllImport vs LibraryImport source generator (разница, преимущества).
- SafeHandle vs IntPtr (почему SafeHandle предпочтительнее).
- Проблемы COM: apartment (STA vs MTA), RCW lifecycle, утечки.
- Как избежать marshalling для производительных сценариев — ручное копирование через `Marshal.Copy` / `Span<byte>`.
