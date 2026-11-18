# Issue

**Title:** Fix missing function in use statement

## Description

A function was missing in use statement with only.

This silently passes in older Fortran standards as it will assume there is an external function with that name.
It fails in our CI pipeline which enforces a newer Fortran standard.

Failure can also be triggered by enforcing explicit typing of external functions

  implicit none (type, external)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec0b2bbfd1b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.