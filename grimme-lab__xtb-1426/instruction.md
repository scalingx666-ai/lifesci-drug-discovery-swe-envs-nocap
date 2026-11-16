# Issue

**Title:** Remove molecular rotation before numerical Hessian

## Description

* While tiny, this causes direct comparison with an externally computed numerical Hessian (or the Hessian reported by the C-API) not to match.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b31754bf3c7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.