# Issue

**Title:** Modify dockstring to not use default logger.

## Description

When dockstring is being used with another program, modifying
the default logger might interfere with other loggers.
Therefore I think it should use its own logger.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ec7f102e5a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.