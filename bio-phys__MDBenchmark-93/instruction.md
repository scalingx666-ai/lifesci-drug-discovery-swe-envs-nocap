# Issue

**Title:** Short option to negate CPU/GPU selection

## Description

Changes made in this pull request:
- Added `-nc` and `-ng` option. This is the short equivalent to `--no-cpu` and `--no-gpu`.

PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [ ] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `62598df16d76`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.