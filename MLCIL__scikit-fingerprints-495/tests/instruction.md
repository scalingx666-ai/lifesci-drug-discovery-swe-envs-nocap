# Issue

**Title:** Optimize tests speed

## Description

## Changes

kNN applicability domain checker had by far the slowest tests. This PR optimizes that by reducing the number of test points. Concrete times are reduced from ~30s to <1s per test.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7eb38dc6e69`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.