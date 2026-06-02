## GitHub Actions
- YAML-конфигурация в `.github/workflows/`.
- **Event** (push, PR) → **Job** (runner) → **Step** (actions).
- Actions Marketplace — готовые шаги (setup-dotnet, docker-login, deploy).
- Matrix build — параллельная сборка (несколько OS, версий .NET).
- **Self-hosted runners** — если нужен кастомный софт или больше ресурсов.
