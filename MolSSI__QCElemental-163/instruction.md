# Issue

**Title:** Model representation

## Description

## Description
Updates the Model reprs to revert back to previous state after Pydantic 1.0 upgrade. This was originally missed in the upgrade. Better tests have been added to prevent this issue in the future.

## Status
- [ ] Changelog updated
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6aa0c2e73cdb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.