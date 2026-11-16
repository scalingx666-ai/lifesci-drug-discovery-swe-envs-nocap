# Issue

**Title:** simplify fp db creation, use new rdkit generators

## Description

- not checking what format every molecule is in iterators
- not generating ids when not available
- using new rdkit fingerprint generators
- drop main.py script

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97904ae81363`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.