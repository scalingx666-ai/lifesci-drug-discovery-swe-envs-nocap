# Issue

**Title:** Fix cumulative best in simulation

## Description

Fixes the bug where the cumbest calculation in the simulation module fails for batch sizes > 1

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `596ae6b673e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.