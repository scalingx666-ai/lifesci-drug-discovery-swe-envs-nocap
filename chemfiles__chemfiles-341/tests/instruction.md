# Issue

**Title:** Make sure CHEMFILES_WINDOWS is defined on chemfiles installation

## Description

Instead of relying on cmake to set `CHEMFILES_WINDOWS`, set it in `include/chemfiles/config.h` when installing the library.

This should fix #333.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f31fb064741`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.