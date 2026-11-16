# Issue

**Title:** Fix plotting bug

## Description

Changes made in this pull request:
- Add check whether the CSV file uses `module` or `gromacs` (old format) as the respective column name.

PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5d6d00aa97e1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.