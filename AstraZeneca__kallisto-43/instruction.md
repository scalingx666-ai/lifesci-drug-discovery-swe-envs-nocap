# Issue

**Title:** Patch SciPy import error and bump version to 1.0.8

## Description

This patch fixes import errors in the `rmsd` module due to a change in [scipy.sparse.linalg.eigsh](https://docs.scipy.org/doc/scipy/reference/generated/scipy.sparse.linalg.eigsh.html).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2290ba6853f0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.