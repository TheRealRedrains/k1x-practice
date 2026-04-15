# k1x-practice

GitOps practice repo for ArgoCD interview prep.

## Structure
- apps/          - ArgoCD Application manifests (app-of-apps pattern)
- services/      - Kubernetes manifests for each service
  - api/         - HEALTHY: nginx, correct resources
  - frontend/    - HEALTHY: nginx, correct resources
  - worker/      - BROKEN: bad image tag (nginx:thistagdoesnotexist)
  - database/    - BROKEN: CPU request too high (2000m, node only has ~2 CPUs)

## Errors to find and fix
1. worker: ImagePullBackOff - fix image tag to nginx:1.25
2. database: Pending pod - fix CPU from 2000m to 100m
