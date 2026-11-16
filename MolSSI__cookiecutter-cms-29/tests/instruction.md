# Issue

**Title:** Changes conda to always_yes

## Description

Sets Conda always_yes so that builds do not hang if a user/developer forgets to add --yes to every command. We could potentially purge all --yes from other parts of the code as well.

Had some odd head state due to the way the last commit/PR was made. It was easier to nuke and remake rather than fix.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3dc7998226c1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.