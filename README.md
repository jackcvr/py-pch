# My python pre-commit hooks

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
      - id: check-json
      - id: check-toml
      - id: debug-statements
      - id: check-added-large-files

  # imports sorting
  - repo: https://github.com/pycqa/isort
    rev: 5.13.2
    hooks:
      - id: isort
        args: [--profile, black]  # use black as the most compatible with ruff

  # linter and formatter
  - repo: https://github.com/astral-sh/ruff-pre-commit
    rev: v0.3.4
    hooks:
      - id: ruff
        args: [--fix]
      - id: ruff-format

  # static type checker
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

  # security checker
  - repo: https://github.com/PyCQA/bandit
    rev: 1.7.8
    hooks:
      - id: bandit
        exclude: tests/

```
