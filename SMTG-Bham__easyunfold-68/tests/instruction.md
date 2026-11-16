# Issue

**Title:** `numpy` `v2` compatibility

## Description

This PR adds a small modification to `easyunfold` to be compatible with `numpy` >=2 (while still being compatible with v1).

Many mat sci packages are now supporting `numpy` v2 (e.g. `pymatgen`), but `easyunfold` currently sets a hard requirement for it to be v1 which is very restrictive for many people's environments. I have updated this and the other requirements here, as I think this is the better choice for avoiding issues as other packages are further developed. Of course open to dissenting arguments!

Closes 

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->
## Summary by CodeRabbit

* **Bug Fixes**
  * More robust boolean matching in overlap and index calculations for improved correctness.

* **Chores**
  * Updated author contact information.
  * Relaxed dependency version constraints to broaden environment compatibility.
  * Bumped package version to 0.4.0.

* **Tests**
  * Reorganized a test helper for plot validation with no behavior change.

* **Style**
  * Upgraded code formatter configuration to a newer release.
<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cb3396a720b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.