# Issue

**Title:** update rdkit-pypi to rdkit

## Description

This pull request updates the dependency in molplotly from `rdkit-pypi` to `rdkit`.  Newer RDKit versions are available at the `rdkit` PyPI repository.

I ran all the example notebooks after the change, which seem to work correctly after updating to `rdkit`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98144a967b64`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.