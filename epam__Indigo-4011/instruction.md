# Issue

**Title:** #3972: KET: load a structure with * atoms as a structure

## Description

The KET loader refused '*' in a molecule as a query-only label, so a structure with '*' could be loaded only as a query. In a molecule '*' is now a pseudoatom, as the MOL, SMILES and CDXML loaders make it; in a query it is still the star atom. Other query labels are refused as before.

## Generic request
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name does not contain '#'
- [x] base branch (master or release/xx) is correct
- [x] PR is linked with the issue
- [x] task status changed to "In Review"
- [x] code follows product standards
- [x] regression tests updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c7c5cd981c88`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.