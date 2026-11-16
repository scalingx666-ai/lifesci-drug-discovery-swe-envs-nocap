# Issue

**Title:** Cmake install improvements

## Description

Some linux distributions use `LIB_INSTALL_DIR`/`INCLUDE_INSTALL_DIR` to change the install path. So accept these =)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8cccc5525b83`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.