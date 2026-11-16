# Issue

**Title:** Consolidate all console output into one API

## Description

Related to #38.

We now can change the format of all info, warning and error messages by only changing one specific function. Messages that should _never_ be formatted were left with `click.echo` (one instance, when listing available host templates).

Changes made in this pull request:
- Added internal API to generalize the use of `click.echo`.
- Messages to the user are now displayed via `mdbenchmark.formatting.info`, `mdbenchmark.formatting.warn` and `mdbenchmark.formatting.error`.
- All styling is done in `formatting.py`. We _never_ call `click.style` anymore, as special styling (making text bold) can be applied with the `placeholder` argument. 


PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [x] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `76ee6c312ba5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.