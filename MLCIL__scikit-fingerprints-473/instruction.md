# Issue

**Title:** Fix docs links

## Description

## Changes

Fixed links in the documentation (particularly examples) to properly point to relevant pages on ReadTheDocs hosting.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [ ] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e412750154ba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.