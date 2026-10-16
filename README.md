# workflow-templates

Modèles de workflows GitHub Actions réutilisables.

## Structure

```text
.
├── .github/
│   └── workflows/
│       └── node-ci.yml
└── README.md
```

Les workflows réutilisables doivent se trouver directement dans
`.github/workflows/`.

## Exemple : CI pour Node.js

Le workflow `node-ci.yml` installe les dépendances avec `npm ci` et exécute
`npm test`. Le dépôt appelant doit donc contenir un `package-lock.json` et un
script `test` dans son `package.json`.

Dans le dépôt qui souhaite l'utiliser, créez un workflow appelant :

```yaml
name: CI

on:
  push:
  pull_request:

jobs:
  test:
    uses: propriétaire/workflow-templates/.github/workflows/node-ci.yml@main
    with:
      node-version: '22'
```

Remplacez `propriétaire` par le propriétaire du dépôt. Pour figer une version,
vous pouvez remplacer `@main` par un tag ou un SHA de commit.
