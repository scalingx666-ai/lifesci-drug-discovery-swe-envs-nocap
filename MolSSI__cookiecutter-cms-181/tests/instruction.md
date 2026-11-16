# Issue

**Title:** move branch rename

## Description

The branch rename actually needs to be after the first commit in order to work with older git versions. Not sure how I overlooked this before!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e975462a318`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.