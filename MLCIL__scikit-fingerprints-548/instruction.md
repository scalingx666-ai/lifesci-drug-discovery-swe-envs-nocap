# Issue

**Title:** Fix Butina split & remove approximate option

## Description

## Changes

Fixes Butina clustering algorithm, plus removes the `approximate` option. It can be used to implement Butina clustering in the future though.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `20f1184fcaa0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.