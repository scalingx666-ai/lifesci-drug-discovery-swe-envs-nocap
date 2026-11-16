# Issue

**Title:** Return N unique smiles, not N IDs

## Description

This also fixed a bug where dedup wasn't working if multiple structures had the exact same score and the duplicate smiles weren't next to each other.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0a254f63b633`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.