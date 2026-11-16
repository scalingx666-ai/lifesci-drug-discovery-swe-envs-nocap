# Issue

**Title:** Bump mctc-lib to v0.5.0

## Description

It helps to compile xtb with LLVM Flang.

xtb + OpenMP + tblite works well with LLVM Flang 21.1.1. Some patches of tblite are necessary for compiling which are absent in v0.4.0.  

See also

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fb4c3b50c33f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.