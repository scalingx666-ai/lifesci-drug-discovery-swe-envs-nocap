# Issue

**Title:** Downgrade to warning: unnatural elements do not have major isotopes

## Description

@johnmay, do we want a test for this?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dcd453efbda6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.