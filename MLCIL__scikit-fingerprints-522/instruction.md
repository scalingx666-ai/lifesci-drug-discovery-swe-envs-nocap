# Issue

**Title:** InChI string support in ``ensure_mols``

## Description

## Changes

Call ``MolFromInchi`` from RDKit if an element of the input sequence to ensure_mols starts with "InChI=".

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)
- [x] Sphinx docs added/updated and render properly (`make docs` and see `docs/_build/index.html`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9527e92acb07`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.