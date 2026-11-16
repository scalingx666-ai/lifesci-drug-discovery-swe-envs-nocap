# Issue

**Title:** add rtd support to cookiecutter

## Description

This is a version of #93 which has a cleaner history

This PR adds creation of files related to hosting documentation on RTD.

Currently, docs use autodoc to pull docstrings from functions. This will work both locally and on RTD if the package has no dependencies. However, if the package has dependencies, RTD needs a yaml file which points to a yaml for a conda environment where dependencies are specified.

This PR implements the following changes

 - A RTD yaml and environment file are added
 - The option to create a RTD yaml and documentation environment file are added to the CookieCutter prompt. If 'no' is selected, the files outlined above are removed.
- Some additional instructions are added to `docs/README.md` if RTD support is chosen.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96997e8179a3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.