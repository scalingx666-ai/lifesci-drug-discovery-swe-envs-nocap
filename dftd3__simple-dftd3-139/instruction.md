# Issue

**Title:** Small optimization of atm.f90

## Description

This patch saves 30 ms per each energy evaluation for 600 atomic system just like changes between `schedule(dynamic,32) collapse(2)` and `schedule(dynamic)`. It is ~7% of total time.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be6c011c03fe`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.