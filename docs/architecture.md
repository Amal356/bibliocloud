# Architecture — BiblioCloud

> Document de travail — sera détaillé en semaine 2 (conception).

## Vue d'ensemble

```
                    ┌──────────────┐
   Utilisateur ───▶ │   Ingress    │
                    └──────┬───────┘
          ┌────────────────┼──────────────────┐
          ▼                ▼                  ▼
  ┌──────────────┐ ┌────────────────┐ ┌─────────────────────┐
  │ auth-service │ │ catalog-service│ │ notification-service│
  │  (Node.js)   │ │   (FastAPI)    │ │      (Node.js)      │
  └──────┬───────┘ └───────┬────────┘ └──────────┬──────────┘
         ▼                 ▼                     ▼
    PostgreSQL        PostgreSQL              MongoDB
```

## Communication inter-services

- `catalog-service` vérifie le token JWT émis par `auth-service`
- `catalog-service` appelle `notification-service` (REST) lors d'un emprunt / retour
- Chaque service expose `/health` (sondes Kubernetes) et `/metrics` (Prometheus)

## Chaîne DevOps

```
commit/push → GitHub Actions : build → tests → docker build → Trivy (échec si CRITICAL)
→ push image (GHCR) → mise à jour du tag dans k8s/ → ArgoCD synchronise le cluster
→ Prometheus collecte /metrics → Grafana (dashboards + alertes)
```
