# Issue

**Title:** Harmonize `float` Related Converters and Validators in Constraints and Conditions

## Description

Due to missing converters, exotic type usage could break the serialization (see issue).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `21ea72fe15b6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.