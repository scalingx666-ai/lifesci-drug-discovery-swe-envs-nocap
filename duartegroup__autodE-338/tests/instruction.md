# Issue

**Title:** DHS improvements

## Description

Fixes recursion error in DHS/DHSGS. Also adds a fallback steepest descent step in case constrained quasi-Newton step cannot be calculated.


***

## Checklist

* [ ] The changes include an associated explanation of how/why
* [ ] Test pass
* [ ] Documentation has been updated
* [ ] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0ff0e5fd7bd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.