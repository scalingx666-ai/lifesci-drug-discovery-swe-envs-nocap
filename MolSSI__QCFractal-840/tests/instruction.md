# Issue

**Title:** Better handling of passwords in init-db

## Description

<!-- Thank you for your contribution! -->

## Description
Before, the database password was written to a temporary file to be read by init-db. This PR fixes that.

This PR also makes database passwords mandatory in the configuration file.

This is only really relevant if `own=True`. If you have an existing db initialized with the previous code, you will need to set the username to the username of your computer, and the password to any arbitrary string. Or backup/restore.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19c1171aad8f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.