# Issue

**Title:** Add python environment check

## Description

Changes made in this pull request:
- Added a function that tries to import `datreant.core`, `datreant.data` and `mdsynthesis` and throws an error at the user, asking to uninstall these python packages.

PR Checklist
------------
 - [x] Update documentation
 - [x] Added unit tests
 - [x] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90a415ce7866`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.