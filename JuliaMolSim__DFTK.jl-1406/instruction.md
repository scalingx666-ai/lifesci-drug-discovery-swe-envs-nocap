# Issue

**Title:** Fix the phase of the Q vectors in the QR retraction

## Description

This ensures that it is always first order accurate. Note that `sign(x)` works just fine for complex numbers, for which it will return the unit phase.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3209c4f2d56`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.