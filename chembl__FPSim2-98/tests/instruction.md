# Issue

**Title:** fix cuda engine

## Description

- fix cuda engine
- make the package compatible with sqlalchemy >= 1.4.7
- try/except for inchi parsing (because of rdkit crashes)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bed59f4e709d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.