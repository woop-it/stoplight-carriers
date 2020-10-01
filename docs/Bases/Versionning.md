---
tags: ['Bases']
---

# Versionning

Un versioning par **header HTTP** est utilisé sur toutes les APIs.

Le header `x-api-version` doit être envoyé à chaque appel avec **la version d'API ciblée**.

Exemple :
```json
{
  "x-api-version": "1.3.0"
}
```

*Les numéros de version suivent la convention. Suivre le lien pour plus de détails sur la Semantic Versioning : [semver](https://semver.org/)*.