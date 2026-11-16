# Issue

**Title:** fix docs and run them in the ci

## Description

The docs pipeline failed because there was a pip check in there, the pixi environment does not have pip and it is not needed either. 

To prevent stuff like this in the future, the docs pipeline apart from the publishing now runs as well if any relevant code is changed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `feae1a9e7e0b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.