# 📚 BiblioCloud — Plateforme de gestion de bibliothèque (microservices + DevOps)

Projet semestriel — **Master DevOps & Cloud, ISET Tozeur** — Année 2026/2027
Module : Projet Annuel 2

**Binôme :** Amal Jemli · Soulayma Hablani

---

## 🎯 Objectif

Concevoir une application web de gestion de bibliothèque en **architecture microservices**, entourée d'une **chaîne DevOps complète et automatisée** :

```
Jira (backlog) → GitHub (code + PR) → GitHub Actions (build + tests)
→ Docker (images) → Trivy (scan sécurité) → Registry (publication)
→ ArgoCD (GitOps) → Kubernetes (déploiement) → Prometheus + Grafana (supervision)
```

## 🧩 Microservices

| Service | Rôle | Techno (proposée) | Persistance |
|---|---|---|---|
| `auth-service` | Inscription, connexion, gestion des utilisateurs et rôles (JWT) | Node.js / Express | PostgreSQL |
| `catalog-service` | Catalogue de livres, recherche, emprunts et retours | Python / FastAPI | PostgreSQL |
| `notification-service` | Notifications (confirmation d'emprunt, rappel de retour, retard) | Node.js / Express | MongoDB |

Chaque service possède sa propre base de données et est **déployable indépendamment**.

## 🛠️ Chaîne d'outils

| Catégorie | Outil retenu |
|---|---|
| Gestion de projet Agile | Jira (Scrum) |
| Code source | GitHub |
| Intégration continue | GitHub Actions |
| Conteneurisation | Docker |
| Scan de sécurité | Trivy |
| Orchestration | Kubernetes |
| Déploiement continu (GitOps) | ArgoCD |
| Supervision | Prometheus + Grafana |

## 📁 Structure du dépôt (mono-repo)

```
bibliocloud/
├── services/
│   ├── auth-service/          # Microservice utilisateurs / authentification
│   ├── catalog-service/       # Microservice catalogue & emprunts
│   └── notification-service/  # Microservice notifications
├── k8s/                       # Manifests Kubernetes (Deployment, Service, ConfigMap, Secret, Ingress)
├── argocd/                    # Applications ArgoCD (GitOps)
├── monitoring/                # Config Prometheus, dashboards Grafana, règles d'alerte
├── docs/                      # Architecture, schémas, rapport
└── .github/                   # Workflows CI, template de Pull Request
```

## 🌿 Stratégie de branches

Nous utilisons **GitFlow simplifié** — voir [CONTRIBUTING.md](CONTRIBUTING.md).

- `main` : version stable, déployée en production (protégée)
- `develop` : intégration continue des fonctionnalités
- `feature/BIB-<n>-<description>` : une branche par user story Jira

Toute modification passe par une **Pull Request revue par l'autre membre du binôme**.

## 📅 Planning

| Semaine | Phase |
|---|---|
| S1 | Cadrage, backlog Jira, dépôt GitHub |
| S2 | Conception de l'architecture |
| S3–S4 | Développement des microservices |
| S5 | Conteneurisation (Docker, docker-compose) — *revue mi-parcours* |
| S6 | Intégration continue + Trivy |
| S7 | Orchestration Kubernetes |
| S8 | GitOps avec ArgoCD |
| S9 | Supervision Prometheus / Grafana |
| S10 | Finalisation, rapport, démonstration |

## 🔗 Liens

- Backlog Jira : _à compléter_
- Architecture : [docs/architecture.md](docs/architecture.md)
