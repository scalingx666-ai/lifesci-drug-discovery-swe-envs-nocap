# Issue

**Title:** Fix pre-commit CI: upgrade pylint to >=3.0 for Python 3.14 compatibility

## Description

Pylint 2.11.x uses `astroid` which references `ast.Str` — removed in Python 3.12. The pre-commit CI job runs Python 3.14, causing pylint to crash immediately before any analysis.

## Changes

- **`pyproject.toml`**: Relax `pylint~=2.11` → `pylint>=3.0` in `pre-commit` extras. Pylint 3.x ships astroid 3.x which is compatible with Python 3.12+.
- **`.pylintrc`**: Disable `too-many-positional-arguments` (R0917) — a new check introduced in pylint 3.x with a default limit of 5 that the existing codebase widely exceeds, and which was never enforced under pylint 2.x.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ffb1a3fb5c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.