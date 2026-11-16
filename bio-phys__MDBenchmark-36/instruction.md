# Issue

**Title:** Update project internals

## Description

Changes made in this pull request:
- Added `Makefile` to project.
- Updated help text and docstrings for `generate`, `submit` and `analyze`.
- Rephrased and formatted messages printed to the console.
- `mdbenchmark generate` will now _first_ look for the `.tpr` file and only then do everything else.
- Added unit tests for all messages generated via `click.echo()` and `click.BadParameter()`.
- Add unit test for `guess_ncores()` utility function.

PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - ~[ ] Issue raised/referenced?~

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `baef9992b159`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.