# Issue

**Title:** CompatHelper: bump compat for Spglib to 1, (keep existing compat)

## Description

This pull request changes the compat entry for the `Spglib` package from `0.9.4` to `0.9.4, 1`.
This keeps the compat entries for earlier versions.

Note: I have not tested your package with this new compat entry.
It is your responsibility to make sure that your package tests pass before you merge this pull request.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cdd9f72bd8b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.