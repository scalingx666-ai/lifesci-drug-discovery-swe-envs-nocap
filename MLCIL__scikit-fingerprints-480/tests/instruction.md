# Issue

**Title:** Add TOPKAT and PROB-STD methods with tests

## Description

## Changes

Added `PROB-STD` and `TOPKAT` applicability domain (AD) checkers, and provided tests. Part of  

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac8ec939f10a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.