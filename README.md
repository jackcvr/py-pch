# Python pre-commit hooks

```
repos:

  # common useful hooks
  - repo: https://github.com/pre-commit/pre-commit-hooks
    rev: v4.5.0
    hooks:
      - id: trailing-whitespace
      - id: end-of-file-fixer
      - id: check-ast
      - id: check-yaml
        args: [--unsafe]
      - id: check-json
      - id: check-toml
      - id: debug-statements
      - id: check-added-large-files

  # linter and formatter (Drop-in parity with Flake8, isort, and Black)
  - repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.3.4
    hooks:
      - id: ruff
        args: [--fix]
      - id: ruff-format

  # static type checker (mypy or pyright?)
  - repo: https://github.com/pre-commit/mirrors-mypy
    rev: v1.9.0
    hooks:
      - id: mypy
        additional_dependencies:
          - types-PyYAML
        args: [
          --no-strict-optional,
          --ignore-missing-imports,
          --follow-imports=skip
        ]

  # security linter
  - repo: https://github.com/PyCQA/bandit
    rev: 1.7.8
    hooks:
      - id: bandit
        exclude: tests/
```
