# Issue

**Title:** Create missing parent directories for server and database log files

## Description

If the configured server logfile or (owned) database logfile was in a directory that did not exist, startup failed: logging.FileHandler raised FileNotFoundError, and pg_ctl failed with "Directory nonexistent", which broke init-db on a fresh instance.

Create the parent directory before opening the server log and before running pg_ctl start. If it can't be created, raise a RuntimeError that names the directory and the reason.

Assisted-by: claude-code/2.1.295:claude-opus-5-5

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3309f94f9ddd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.