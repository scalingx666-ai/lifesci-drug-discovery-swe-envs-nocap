# Issue

**Title:** Update analyze CSV output settings

## Description

Changes made in this pull request:
- saner csv output names
- default behavior of analyze changed such that by default no csv is saved.
- when invoking ```--save-csv``` a file is saved


PR Checklist
------------
 - [ ] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [x] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `20d1e7f6a772`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.