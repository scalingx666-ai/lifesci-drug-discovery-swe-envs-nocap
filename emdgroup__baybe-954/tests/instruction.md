# Issue

**Title:** Silence all pandas 4 deprecation warnings

## Description

More warnings showed up, and it is expected that the number keeps growing. So we disable all of them at once, desperately looking forward to the upcoming narwhals merge ;)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ed54e0092acd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.