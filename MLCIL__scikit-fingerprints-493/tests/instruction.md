# Issue

**Title:** Optimize conformer generator

## Description

## Changes

Simplified and optimized the `ConformerGenerator` class. It now uses ETKDGv3 -> KDG -> DG as fallbacks, with random starting coordinates. This maximizes the robustness. I also included `suppress_warnings` and `timeout` parameters for more fine-grained control.

This reduces the time 2-5 times, depending on the data. It also is much more robust to "bad" molecules, and setting timeout ensures quite uniform time across different molecules.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b7eb38dc6e69`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.