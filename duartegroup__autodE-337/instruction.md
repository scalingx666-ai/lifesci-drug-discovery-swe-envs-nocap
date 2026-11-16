# Issue

**Title:** Refactor Hessian update

## Description

Puts the hessian update into the coordinate object. This is for consistency with the `update_h_from_cart_h` method and for future modification of the optimiser loop.

***

## Checklist

* [x] The changes include an associated explanation of how/why
* [x] Test pass
* [x] Documentation has been updated
* [x] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b3e77267380`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.