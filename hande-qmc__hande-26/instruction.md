# Issue

**Title:** Use CMake 3.6.3 on Travis

## Description

Force usage of the minimum required CMake version (3.6) on Travis. This should ensure that the requirement is not accidentally broken because of a more modern CMake version available on the CI image.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3765427f4e37`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.