# Issue

**Title:** Fix: Submit summary

## Description

Changes made in this pull request:
- Changed order of code, so that the submit summary only considers benchmarks that were not submitted yet.


PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [x] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fe97eea22361`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.