# CI/CD Pipelines

## GitHub Actions
- YAML-конфигурация в `.github/workflows/`.
- **Event** (push, PR) → **Job** (runner) → **Step** (actions).
- Actions Marketplace — готовые шаги (setup-dotnet, docker-login, deploy).
- Matrix build — параллельная сборка (несколько OS, версий .NET).
- **Self-hosted runners** — если нужен кастомный софт или больше ресурсов.

## Azure DevOps
- YAML или Classic Editor. Pipeline → Stage → Job → Task.
- **Agent pools** — Microsoft-hosted / self-hosted.
- **Artifacts / Packages** — NuGet, npm в Azure Artifacts.
- **Release Pipeline** — отдельный пайплайн деплоя (Classic) или multi-stage YAML.

## GitLab CI
- `.gitlab-ci.yml` — stages (build, test, deploy).
- **Runners** — Docker, Kubernetes, Shell.
- **GitLab Container Registry** — встроенный Docker registry.

## Общее
- **CI**: build → lint → test → publish артефактов.
- **CD**: deploy → smoke tests → health check.
- Аналог: TeamCity, Jenkins, CircleCI, Bitbucket Pipelines.

## Важно для интервью
- Secrets — не хардкодить, использовать переменные окружения (secrets).
- Garded rollout — постепенный деплой для снижения риска.
- Blue-green / Canary deployment — стратегии деплоя.
