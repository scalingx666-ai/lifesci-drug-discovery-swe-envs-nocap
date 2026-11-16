# Issue

**Title:** Fix global D4 reference charge table overwrite

## Description

In `newD4Model`, a leftover `select case(mode)` block overwrote the module-level `refq` and `refh` arrays, overwriting defaults in a second calculation. Since the selection block was unnecessary anyway, I removed it.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e20416b1a436`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.