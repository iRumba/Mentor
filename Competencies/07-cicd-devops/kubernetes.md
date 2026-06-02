# Kubernetes

## Основные объекты
- **Deployment** — управляет ReplicaSet, обеспечивает rolling update, масштабирование.
- **Service** — стабильный endpoint для доступа к Pod'ам (ClusterIP, NodePort, LoadBalancer).
- **ConfigMap** — конфигурация (не секретная). **Secret** — секретные данные (base64, encrypted).
- **Ingress** — HTTP/HTTPS routing (внешний доступ).
- **Namespace** — виртуальный кластер.

## Обновление и масштабирование
- **Rolling Update** — постепенная замена Pod'ов (без downtime).
- **Horizontal Pod Autoscaler (HPA)** — автоматическое масштабирование по CPU/memory/custom metrics.
- **livenessProbe / readinessProbe** — health checks.

## Хранение данных
- **PersistentVolume (PV)** — ресурс хранения.
- **PersistentVolumeClaim (PVC)** — запрос на хранение.
- **StatefulSet** — для stateful приложений (БД) с уникальными именами и стабильными volume'ами.

## Sealed Secrets
- **SealedSecret** — Custom Resource: шифрует Secret для хранения в Git.
- Работает через `kubeseal` CLI + Sealed Secrets Controller в кластере.
- Безопасное хранение секретов в репозитории.

## Важно для интервью
- Pod — минимальная единица. Containers в Pod'е делят network и storage.
- Service Mesh (Istio, Linkerd) — дополнительный слой для traffic management, mTLS, observability.
- Helm — пакетный менеджер для Kubernetes (chart →release).
- kubectl — основной инструмент управления.
