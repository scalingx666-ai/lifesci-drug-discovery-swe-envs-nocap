# Issue

**Title:** Add build support for Intel OneAPI / LLVM compilers

## Description

This PR adds support for building with Intel OneAPI compilers (LLVM-based) and resolves issues when building with Intel MPI libraries.

*Note*: the aforementioned supported added in this PR  comes from pulling inupdates from AmberTools build system.  As this is currently still actively developed, this may require further updates.

Related: #327

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `45db608b52b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.