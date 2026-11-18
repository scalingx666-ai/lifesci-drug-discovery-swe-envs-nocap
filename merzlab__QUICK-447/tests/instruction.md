# Issue

**Title:** Fix build report message

## Description

Trivial fix in Cmake build system if statement: Do not print compilation time warning for f function code if not building GPU code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe3c92849f8d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.