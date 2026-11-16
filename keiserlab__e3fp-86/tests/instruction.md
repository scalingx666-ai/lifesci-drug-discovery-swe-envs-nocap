# Issue

**Title:** Include license file in source distribution

## Description

It seems that using the `pyproject.toml` our `MANIFEST.in` is being ignored. That's fine, it's outdated anyways (this PR removes it). But this does mean that `LICENSE.txt` was not being packaged with the source distribution, which the conda-forge recipe doesn't like (https://github.com/conda-forge/e3fp-feedstock/tree/main/recipe). By specifying the license by filename, it is now added to the source distribution.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f2acb44a016`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.