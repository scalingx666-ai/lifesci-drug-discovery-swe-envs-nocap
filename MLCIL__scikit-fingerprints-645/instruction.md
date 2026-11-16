# Issue

**Title:** Mordred Pipeline Fix

## Description

## Changes

This pull request updates the dataset fetching logic to ensure that data files are always downloaded if they do not already exist, even if the `force_update` flag is not set. This prevents errors when files are missing and improves the robustness of the dataset utilities.

## Checklist before requesting a review
- [ ] Docstrings added/updated in public functions and classes
- [ ] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [ ] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2d2eb8cb7724`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.