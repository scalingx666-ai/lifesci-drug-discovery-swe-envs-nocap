# Issue

**Title:** Models: Minor basis fix if center data is not valid

## Description

Validation would fail with an incorrect error message if `center_data` did not validate in Basis. This PR fixes this issue to always ensure validation errors are thrown at the correct location.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e2bbb10ec67`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.