# Issue

**Title:** test: bring coverage to 100%

## Description

## Summary
- adds tests for cli, helpers, molecule, visualization, and remaining graph branches; 58% → 100%
- makes Atom hashable via `eq=False` so `Bond.atoms` and `Bond.__contains__` actually work
- shared `WATER_XYZ` and `water_molecule` fixture moved to `tests/conftest.py`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7b8e50972fc2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.