# Issue

**Title:** Bugfix for more than 2 species in complex

## Description

Atom order was not maintained when more than two species were added to a complex. This bugfix resolves that.


***

## Checklist

* [ ] The changes include an associated explanation of how/why
* [ ] Test pass
* [ ] Documentation has been updated
* [ ] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e8b06a96b3a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.