# Issue

**Title:** Implement random seed behavior

## Description

Fix nondeterministic seed behavior originally mentioned in #203. 
Implemented random seed behavior according to .
Random seed can now be supplied by the user via CLI or config file. Seed from CLI has priority.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66dd249a17af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.