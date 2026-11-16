# Issue

**Title:** Prevent division by zero in betas_liquid methods

## Description

Three methods in EquilibriumState would raise a ZeroDivisionError when
called with no liquid phases present.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd274271a618`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.