# Issue

**Title:** Clean up session information for deleted models

## Description

Track served models with their session info so if they are deleted while being served, we can safely remove their session data. This ensures that command such as `ersilia info`, and `ersilia example` do not pick up residual session information for models that don't even exist on the user's system.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ad004a309329`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.