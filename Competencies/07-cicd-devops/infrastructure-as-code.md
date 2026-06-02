# Infrastructure as Code (IaC)

## Что такое IaC
- Управление инфраструктурой через конфигурационные файлы (а не ручные CLI/UI).
- Версионирование, воспроизводимость, code review для инфраструктуры.
- Два подхода: **Declarative** (что нужно) и **Imperative** (как сделать).

## Terraform
- **HashiCorp Terraform** — самый популярный IaC инструмент.
- HCL (HashiCorp Configuration Language) — декларативный язык.
- `terraform plan` → `terraform apply` → `terraform destroy`.
- State management — локальный/удалённый (S3, Azure Storage, Terraform Cloud).
- Providers: Azure, AWS, GCP, Kubernetes, GitHub, Datadog, и сотни других.
- **Modules** — переиспользуемые блоки инфраструктуры.

## Bicep (Azure)
- **Azure Bicep** — декларативный DSL для Azure Resource Manager (ARM).
- Транспилируется в ARM JSON. Лаконичнее ARM-шаблонов.
- Работает только с Azure (не кроссплатформенный).

## Pulumi
- IaC на привычных языках: C#, TypeScript, Python, Go.
- Использует обычные языки: циклы, условные операторы, функции.
- State management — Pulumi Cloud / self-managed.
- Кроссплатформенный: Azure, AWS, GCP, Kubernetes.

## Важно для интервью
- Terraform — индустриальный стандарт (multicloud).
- Terraform vs Pulumi — DSL vs real programming language.
- State locking — для командной работы.
- Drift detection — план показывает различия между кодом и реальностью.
