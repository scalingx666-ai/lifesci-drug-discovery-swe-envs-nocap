# Issue

**Title:** Add mordred aromatic count descriptors

## Description

## Changes

* Added new `aromatic` descriptor module (`skfp/fingerprints/_new_mordred/descriptors/aromatic.py`) that computes the number of aromatic atoms and bonds using RDKit's aromaticity flags.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `745bba4c7e70`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.