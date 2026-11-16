# Issue

**Title:** Automatic differentiation for primitives

## Description

Replaces hand-coded derivatives for primitive internals with automatic differentiation so that upto second derivatives can be calculated for any primitive.


***

## Checklist

* [ ] The changes include an associated explanation of how/why
* [ ] Test pass
* [ ] Documentation has been updated
* [ ] Changelog has been updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c4a02113f3f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.