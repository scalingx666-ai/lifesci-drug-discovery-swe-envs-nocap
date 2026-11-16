# Issue

**Title:** Add HP tuning scikit-fingeprint vs scikit-klearn benchmark

## Description

## Changes

Implemented a benchmark to compare execution time, relative and absolute gain, and ROC AUC between hyperparameter tuning pipelines in scikit-fingerprints and scikit-learn.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `533a42ee4941`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.