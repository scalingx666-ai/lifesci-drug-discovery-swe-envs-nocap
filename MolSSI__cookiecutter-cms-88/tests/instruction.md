# Issue

**Title:** remove comma from try/except that was causing error if no README

## Description

There was a comma at the end of one line which was causing an error with install if there was no README. 

Addresses #87

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67cfcd198285`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.