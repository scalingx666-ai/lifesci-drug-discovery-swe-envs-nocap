# Issue

**Title:** Fix: plotting crash on unfinished benchmark

## Description

Changes made in this pull request:
- Make sure the plotting does not crash, when some benchmarks are not finished yet.
- Removed obsolete test and corresponding test files.

PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [x] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `876568c14294`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.