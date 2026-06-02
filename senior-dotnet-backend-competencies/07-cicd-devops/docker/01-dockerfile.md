## Dockerfile
- Инструкция для сборки образа. Каждая инструкция — слой (layer).
- **Multi-stage build** — отдельные этапы: сборка (SDK) → рантайм (runtime-only).
- Пример: `FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build` → `dotnet publish` → `FROM mcr.microsoft.com/dotnet/aspnet:8.0`.
