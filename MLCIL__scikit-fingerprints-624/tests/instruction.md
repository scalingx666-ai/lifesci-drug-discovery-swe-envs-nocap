# Issue

**Title:** Update dependencies

## Description

## Changes

Update dependencies. Also turns off a PyTorch vulnerability which has no fix, and is a very rare edge case, I don't think it's relevant at all to scikit-fingerprints.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8cf52ab56a21`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.