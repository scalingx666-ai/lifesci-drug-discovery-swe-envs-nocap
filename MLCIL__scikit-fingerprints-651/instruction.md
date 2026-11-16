# Issue

**Title:** Mordred DistanceMatrix

## Description

## Changes

This pull request adds a new implementation for the "distance matrix" descriptors in the new Mordred fingerprint code, fixes the computation of the LogEE descriptor to match its documented formula, and updates tests and reference data accordingly. The changes ensure that the LogEE descriptor now computes the mathematically correct value, diverging from the legacy mordred-community and PaDEL implementations, and that this divergence is correctly handled and documented in the test suite.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4568a2f8195f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.