# Issue

**Title:** Pubchem feature names

## Description

## Changes

Added feature (descriptor) names for PubChem fingerprint, part of  I refactored patterns to a separate files, since they alone take ~1000 lines.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `693d4ea4b7f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.