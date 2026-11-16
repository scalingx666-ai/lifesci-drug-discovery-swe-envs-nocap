# Issue

**Title:** Mordred CPSA

## Description

## Changes

This pull request introduces the Charged Partial Surface Area (CPSA) descriptors to the `_new_mordred` fingerprint module, implements their calculation, and adds comprehensive tests and reference data to ensure correctness. It also refactors utility functions for per-atom operations and surface area calculations to improve code clarity and reusability.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad8ffa60059d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.