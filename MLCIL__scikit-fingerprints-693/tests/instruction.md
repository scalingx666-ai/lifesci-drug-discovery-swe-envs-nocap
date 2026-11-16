# Issue

**Title:** Drop support for Python 3.10

## Description

## Changes

Python 3.10 reaches end of life in October 2026, and some new features (such as `CheMeleon` fingerprints) can't be supported on it. Users who need Python 3.10 can continue to use scikit-fingerprints 2.1.0

## Checklist before requesting a review
- [X] Docstrings added/updated in public functions and classes
- [X] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [X] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c2cdfb6c4046`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.