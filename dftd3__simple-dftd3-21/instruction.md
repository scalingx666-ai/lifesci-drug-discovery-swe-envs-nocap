# Issue

**Title:** replace deprecated `make_directory` with `file(MAKE_DIRECTORY)`

## Description

https://cmake.org/cmake/help/v3.14/command/make_directory.html

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d76ce4037540`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.