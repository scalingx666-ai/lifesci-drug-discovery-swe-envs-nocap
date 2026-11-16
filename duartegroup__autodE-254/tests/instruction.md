# Issue

**Title:** Fix RFO hessian update bug

## Description

##  

Hessian is updated in RFO, as Hessian is used for step instead of augmented Hessian
***

## Checklist

* [x] The changes include an associated explanation of how/why
* [x] Test pass
* [x] Documentation has been updated
* [x] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1f42142f5a11`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.