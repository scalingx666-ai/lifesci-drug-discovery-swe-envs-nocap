# Issue

**Title:** Add `only_explicit` parameter to `require_atoms` decorator

## Description

The `require_atoms` decorator now supports a new `only_explicit` flag to optionally include implicit hydrogens in atom count checks. Updated the validation logic and added comprehensive tests to cover this functionality. This change ensures more flexible molecule validation.

## Changes

*Short description of changes*

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `946096945303`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.