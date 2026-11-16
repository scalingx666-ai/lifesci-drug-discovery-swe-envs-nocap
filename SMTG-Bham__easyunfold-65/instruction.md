# Issue

**Title:** Fix bug caused by floating point

## Description

This PR should fix #64 which was caused by incorrect G vector returned by the `find_K_from_k` function due to floating point rounding. 

Changes included in this PR:
* Use `np.allclose` for checking equality for floating point numbers. 
* Fix a bug where the G vector calculated can be wrong due to floating point rounding.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

* **Bug Fixes**
  * Improved numerical accuracy when deriving reciprocal-space integer vectors by rounding before integer conversion.
  * Standardized floating‑point comparisons with a small tolerance to make k‑point uniqueness and reduction more robust.

* **Tests**
  * Updated tests to verify k‑points using approximate per‑point membership checks, allowing for reordering and time‑reversal equivalence.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4dc31a5f3c5d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.