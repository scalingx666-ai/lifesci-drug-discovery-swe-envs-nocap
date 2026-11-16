# Issue

**Title:** Add pre-commit configuration file

## Description

## Description

Add [pre-commit](https://pre-commit.com/) configuration file. This allows to install pre-commit `git` hooks (`pre-commit install`) so that every commit runs the same checks as CI (`black`, `flake8`, `isort`, `mypy`).

## Checklist

- [x] Documentation
- [x] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c5d8870ac1d1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.