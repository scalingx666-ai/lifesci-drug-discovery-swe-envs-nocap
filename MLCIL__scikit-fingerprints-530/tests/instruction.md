# Issue

**Title:** Add Tanimoto scikit-fingerprints vs RDKit benchmark

## Description

## Changes

Implement SKFP vs RDKit benchmark comparing speed of the Tanimoto distance computation (pairwise).

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a881f2ce4184`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.