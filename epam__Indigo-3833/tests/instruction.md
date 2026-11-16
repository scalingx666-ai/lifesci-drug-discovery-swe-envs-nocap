# Issue

**Title:** #317 making a fix for smiles to support stereochemistry information

## Description

This is implementation of the fix for the stereochemistry and compare each case against the Biovia specification that describe behavior of the stereo chemistry within case. Took 2 examples and calibrated tests suites against the golden standard provided within Biovia specification document.

## Generic request
- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name does not contain '#'
- [x] base branch (master or release/xx) is correct
- [x] PR is linked with the issue
- [x] task status changed to "Code review"
- [x] code follows product standards
- [x] regression tests updated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `171c3ffa3072`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.