# Issue

**Title:** 2026 04 24

## Description

Two minor fixes.
- abbreviations should allow [2H] when collapsing the whole thing, simply we need to reuse the existing smiles generator field.
- the warning on stereochemistry can be better

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12ef701869b7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.