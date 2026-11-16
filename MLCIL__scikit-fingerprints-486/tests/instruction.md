# Issue

**Title:** MACCS fingerprint fix

## Description

## Changes

With latest RDKit, I was getting segfault error with MACCS -> NumPy conversion. For some reason `np.array()` errors, but `np.vstack()` works without problems.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72d7459c1345`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.