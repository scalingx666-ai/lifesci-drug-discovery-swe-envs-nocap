# Issue

**Title:** Add mypy check to CI and skip ASE tests when package missing

## Description

## Changes
 
 - Add `mypy .` step to the `pre-commit` CI job in `.github/workflows/test.yml`.
 - Remove the commented-out mypy hook from `.pre-commit-config.yaml` (mypy now runs as a dedicated CI step, not via pre-commit).
 - Use `pytest.importorskip("ase")` in `tests/test_ase.py` to skip the whole module when ASE is unavailable, replacing the prior `try/except` + per-test `skipif` decorators.
 - Incidental fixes carried in this branch: `pyproject.toml` and `src/skala/ase/calculator.py`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cea9718b5df5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.