# Issue

**Title:** Fix database constraint violation when program version strings contain uppercase characters

## Description

<!-- Thank you for your contribution! -->

## Description
Some program version strings can contain uppercase characters, which causes a database constraint violation.
This adds normalization for that case (+ a test)



## Changelog description
Fix database constraint violation when program version strings contain uppercase characters

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a929ca8006f4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.