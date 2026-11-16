# Issue

**Title:** Small maintenance

## Description

- Removed scipy from the dependencies in the `setup.py` because it is indeed unused.
    This is necessary for the conda packaging.

- Made URLs in the doc that pointing to images more stable.

- Improved Logo.

- Removed `conda.recipe`. We now do this from the outside with `conda-forge`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fc269da1803d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.