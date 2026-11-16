# Issue

**Title:** Add ResponseVariableRange and StandardDeviation AD checkers with tests

## Description

## Changes

Added `ResponseVariableRange` and `StandardDeviation` applicability domain (AD) checkers, and provided tests.
Also, added missing references to the documentation of the `BoundingBoxADChecker`. Part of  

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b767151dc04`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.