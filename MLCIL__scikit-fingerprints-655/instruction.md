# Issue

**Title:** Mordred Detour Matrix

## Description

## Changes

Adds support for the detour matrix descriptor to the new Mordred fingerprint implementation.

* Added `networkx>=3.4.2` as a new dependency in `pyproject.toml`

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `18ff996d5a56`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.