# Issue

**Title:** Warn about double-bond stereochemistry with macrocycles

## Description

Quite a minor diff; encountered this recently; a logger message (as outlined in the JavaDoc for the class) would have localised this more quickly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `df1a0034c9c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.