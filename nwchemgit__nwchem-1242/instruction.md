# Issue

**Title:** bug fixes in integral codes

## Description

* fix for issue  in integral 1st derivatives with large number of point charges
* fix for numerical instability in Douglas-Kroll code

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b9c2fa81f972`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.