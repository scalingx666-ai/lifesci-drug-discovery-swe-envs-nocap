# Issue

**Title:** Miscellaneous before v0.15.0

## Description

<!-- Thank you for your contribution! -->

## Description
squash a few issues.

## Changelog description
* allow nonphysical masses validation through `from_schema` needed for psi4 findif frequencies.
* add `strict` option to `to_Z`, `to_symbol` and `to_element` so that `"O18"` can error out. Useful when these are used for validation (like `models.Molecule`) and you don't want the user to think their misplaced mass info has been accepted.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f6518803e2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.