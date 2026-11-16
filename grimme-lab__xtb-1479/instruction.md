# Issue

**Title:** Check Orca exit code

## Description

Checks the Orca exit code. This avoids failing on non-fatal Orca errors, which might end up in stderr (this includes MPI problems. Errors are still reported.

Addresses the root cause of #1030

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e1df6f0dcb79`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.