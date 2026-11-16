# Issue

**Title:** Updates

## Description

Features:
- [x] Adds versioneer docs.
- [x] Enhanced checking of python repo name. Tries to make `project_name` default to `ProjectName` to make it more clear that this can have caps and discourages underscores in a name.
- [x] Ensures the CoC does not try to email MolSSI.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5b366d7ad9a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.