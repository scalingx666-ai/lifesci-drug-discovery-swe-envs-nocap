# Issue

**Title:** dirac: fix hash

## Description

Fixes the source hash for Dirac, which somehow has diverged. I suspect `deepClone = true;` to be responsible. There is a bunch of newer releases for Dirac, namely 26.0. However, it requires recreating all patches for the build system.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `61f280b86d64`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.