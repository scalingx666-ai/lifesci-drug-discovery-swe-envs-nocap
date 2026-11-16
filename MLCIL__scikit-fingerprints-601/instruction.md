# Issue

**Title:** Update dependencies

## Description

## Changes

All tests passed locally with updated dependencies, so this should not cause any problems.

Test improvements:

* Updated the type annotation for `X` in `tests/sklearn_compatibility/basic_checks.py` (to make it compatible with new mypy restrictions)

Configuration changes:

* Changed the `allow_redefinition` option to `allow_redefinition_old` in the `[tool.mypy]` section of `pyproject.toml`, to reflect a change in mypy behaviour.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3910e930d62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.