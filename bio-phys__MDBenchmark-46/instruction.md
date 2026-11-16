# Issue

**Title:** Bugfix for generate command

## Description

Changes made in this pull request:
- The message `Creating a total of X benchmarks, with a run time of Y each.` now display the correct number of systems that will be generated.
- `--min-nodes` cannot be bigger than `--max-nodes`. Added an exception and tests.

PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - ~[ ] Issue raised/referenced?~

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4e3a82249095`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.