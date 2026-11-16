# Issue

**Title:** Validation update

## Description

@mimischi this is a possible clean up for your PR

- validation is done in click callbacks if possible
- engine check is done as a normalize option in mdengines.__init__
- the validation module is removed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a53aabcde2a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.