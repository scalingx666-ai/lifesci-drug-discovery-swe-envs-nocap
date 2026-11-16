# Issue

**Title:** Mordred Information Content

## Description

## Changes

This pull request adds a new set of "information content" molecular descriptors to the Mordred-inspired fingerprint calculator, aligning with the mordred-community library. It introduces a new descriptor module, updates the calculator and feature name lists to support these descriptors, and adds comprehensive tests with reference values for validation. Additionally, it standardizes the naming and usage of bond order constants across the codebase.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `acf64a10a376`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.