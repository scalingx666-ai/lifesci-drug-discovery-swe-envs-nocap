# Issue

**Title:** Add CI testing

## Description

Add initial CI testing. It makes the conda env and runs yapf + flake8. However I'm not 100% sure if it will work (not sure how to test it because github runs it).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f13ca1f432f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.