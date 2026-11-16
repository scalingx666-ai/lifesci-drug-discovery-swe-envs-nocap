# Issue

**Title:** Dimension deprecation: std::pair DPD constructor

## Description

## Description
Breaks up #3351

Part of a larger effort to deprecate those pesky Dimension operators. Previously, DPD objects were often created by pushing back two `int *` pointers at a time. The first of these was often of type `Dimension` hence the cast-to-pointer warning. This PR creates a new DPD constructor (and `dpd_init` function) for type `std::vector<std::pair<Dimension, int *>>` and changes all relevant cast-to-pointer cases to use this constructor.

## User API & Changelog headlines
- API: new DPD constructor and `dpd_init` functions. 
- API: Deprecating old DPD constructor.

## Dev notes & details
- See Description

## Checklist
- [x] [All or relevant fraction of full tests run](http://psicode.org/psi4manual/master/build_planning.html#how-to-run-a-subset-of-tests)

## Status
- [x] Ready for review
- [x] Ready for merge

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `382af67892d7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.