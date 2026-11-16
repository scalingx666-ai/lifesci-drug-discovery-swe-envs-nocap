# Issue

**Title:** Add install script for module files

## Description

- use the fact that only the dftd4 library is build at the toplevel
- find all module files in the toplevel directories in the build dir

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `233250fbc2d7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.