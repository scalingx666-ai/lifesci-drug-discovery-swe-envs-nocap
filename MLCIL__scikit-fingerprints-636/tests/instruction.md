# Issue

**Title:** Fix datasets tests

## Description

## Changes

Improves detection of "datasets changed" to avoid running slow tests on CI. Also applies to doctests now. Reduced reruns, I analyzed the CI runs and flaky tests always succeed or fail totally during the first 10 runs.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e504f0aee682`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.