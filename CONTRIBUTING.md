# Règles de contribution

## Branches (GitFlow simplifié)

| Branche | Rôle | Règle |
|---|---|---|
| `main` | Production | Protégée, merge uniquement depuis `develop` via PR |
| `develop` | Intégration | Protégée, merge via PR revue |
| `feature/BIB-<n>-<desc>` | Une user story | Créée depuis `develop` |
| `fix/BIB-<n>-<desc>` | Correction de bug | Créée depuis `develop` |

Exemple : `feature/BIB-12-login-jwt`

## Messages de commit (Conventional Commits)

```
<type>(<service>): <description courte> [BIB-<n>]
```

Types : `feat`, `fix`, `docs`, `test`, `ci`, `build`, `refactor`, `chore`

Exemples :
- `feat(auth): ajout de l'endpoint POST /login [BIB-12]`
- `ci(catalog): ajout du scan Trivy dans le pipeline [BIB-41]`

Mettre la clé Jira (`BIB-12`) dans le commit et le nom de branche permet de lier automatiquement GitHub et Jira.

## Pull Requests

1. Pousser la branche `feature/...`
2. Ouvrir une PR vers `develop` en utilisant le template
3. **L'autre membre du binôme relit et approuve**
4. Le pipeline CI doit être vert avant le merge
5. Supprimer la branche après merge

## Répartition du travail

Chaque membre crée ses propres commits avec son compte GitHub, afin que la répartition soit visible dans l'historique (exigence de l'énoncé).
