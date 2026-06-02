# Docker

## Dockerfile
- Инструкция для сборки образа. Каждая инструкция — слой (layer).
- **Multi-stage build** — отдельные этапы: сборка (SDK) → рантайм (runtime-only).
- Пример: `FROM mcr.microsoft.com/dotnet/sdk:8.0 AS build` → `dotnet publish` → `FROM mcr.microsoft.com/dotnet/aspnet:8.0`.

## Основные инструкции
- `FROM` — базовый образ.
- `WORKDIR` — рабочая директория.
- `COPY` / `ADD` — копирование файлов.
- `RUN` — команда при сборке (dotnet restore, npm install).
- `EXPOSE` — открываемый порт (документация).
- `CMD` / `ENTRYPOINT` — запуск при старте контейнера.

## Docker Compose
- Запуск нескольких контейнеров (app + БД + Redis + ...).
- `docker-compose.yml` — конфигурация сервисов, сетей, томов.
- `depends_on` — порядок запуска. `healthcheck` — проверка готовности.

## Best Practices
- .dockerignore — исключать `bin/`, `obj/`, `.git/`.
- Минимизировать слои — объединять `RUN` команды.
- Использовать специфичные версии, не `latest`.
- Security: не запускать от root, не хранить секреты в образе.

## Важно для интервью
- Docker — процессная виртуализация (контейнеры), а не аппаратная (VM).
- Overlay filesystem — как работают слои.
- Docker Networking — bridge, host, none, overlay.
- Volume vs Bind mount — данные вне контейнера.
