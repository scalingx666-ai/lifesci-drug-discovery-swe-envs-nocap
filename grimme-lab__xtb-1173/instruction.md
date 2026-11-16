# Issue

**Title:** Fix xtb/docking test

## Description

During careful running of xtb/docking test via CMake I have found several divisions by zero and improperly closing of files. This patch resolves such issues

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8631a45f0398`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.