# Issue

**Title:** Fix tests on CI

## Description

## Changes

Try to fix cache for tests on CI, which hasn't been working properly. It was being silently ignored, resulting in no datasets tests in all cases.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `77f3825ca65c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.