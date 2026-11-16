# Issue

**Title:** Refactor tests

## Description

Changes made in this pull request:
- Refactored tests. Got rid of duplicate code, added `@pytest.mark.parametrize` where applicable.

PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - ~[ ] Issue raised/referenced?~

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4007b649795d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.