# Issue

**Title:** Fix: fe and clr not calculated if ae not included in intervals

## Description

Just worthy to mention that the unit tests we do for `pk.calc` function will never cover these cases. Maybe is worthy to consider doing at some point a test for `pk.nca` with a dataset that contains all columns and a for-loop checking all parameters independently.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1d95c4a044e7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.