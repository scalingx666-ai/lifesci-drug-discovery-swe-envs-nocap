# Issue

**Title:** Update build system

## Description

I have fixed fetching HEAD instead of specific revision. Also, IFX 2025.2 is used now in CI for CMake.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3f212ba8328`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.