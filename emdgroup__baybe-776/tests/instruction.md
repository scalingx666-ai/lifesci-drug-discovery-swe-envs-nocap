# Issue

**Title:** Parameter validation for kernel factories

## Description

DevPR, parent is 

Adds a validation mechanism to ensure kernel factories only produce kernels for search spaces they are intended for.
This is achieved via a new `_ParameterKind` flag enum that factories can use to signal which parameter types they support.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9ef2604f9f3b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.