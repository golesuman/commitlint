# commitlint

commitlint is a tool designed to lint your commit messages according to the [Conventional Commits](https://www.conventionalcommits.org/) standard for your pre-commit hook and GitHub Actions.

## How to use

### For pre-commit

1. Add the following configuration on `.pre-commit-config.yaml`.

   ```yaml
   repos:
   ...

   - repo: https://github.com/opensource-nepal/commitlint
       rev: 0.1.0
       hooks:
       - id: commitlint

   ...
   ```

2. Install the `commit-msg` hook in your project repo:

   ```bash
   pre-commit install --hook-type commit-msg
   ```

> **_NOTE:_** Installing using only `pre-commit install` will not work.

### For github-actions

If you have any existing workflows, add the following steps:

```yaml
steps:
    ...
    - name: Run commitlint
    uses: opensource-nepal/commitlint@0.1.0
    ...
```

If you don't have any workflows, create a new GitHub workflow, e.g. `.github/workflows/commitlint.yaml`.

```yaml
name: Commitlint

on:
  push:
    branches: ['main']
  pull_request:

jobs:
  commitlint:
    runs-on: ubuntu-latest
    name: Check commit messages
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Run commitlint
        uses: opensource-nepal/commitlint@0.1.0
```

> **_NOTE:_** commitlint GitHub Actions will only be triggered by "push" or "pull_request" events.

## Contribution

We appreciate feedback and contribution to this package. To get started please see our [contribution guide](./CONTRIBUTING.md).
