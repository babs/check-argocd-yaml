# check-argocd-yaml

This repository contains a pre-commit hook to validate some readability and maintainability check for ArgoCD Application manifests.

For Application manifest, rules are:
* `spec.source` or `spec.sources` must be the last `spec` section
* if `spec.source` or any `spec.sources[*]` is of `helm` type, then `values` and `valuesObject` must be last(s) key(s)

This ensures that most relevant `spec` declarations are at the top of the file, preventing them from being obscured by large `values` or `valuesObject` sections.

## Installation

To use this pre-commit hook, add the following to your `.pre-commit-config.yaml`:

```yaml
  - repo: https://github.com/babs/check-argocd-yaml
    rev: v0.0.1
    hooks:
    - id: check-argocd-app
```

## Usage

```bash
pre-commit run check-argocd-app --all-files
```
