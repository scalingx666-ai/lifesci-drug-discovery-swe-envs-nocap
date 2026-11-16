# Issue

**Title:** 179 update code to new mypy checks

## Description

Solves #179
ToDos:
 - [x] Ignore RDKit type errors
 - [x] Make setters contravariant instead of covariant (did not know this, could not find out why)
 - [x] For contravariance make `count_value_to_tuple` work with `int` and `float`. Renamed to `assure_range`
 - [x] Autoformatting with pre-commit hook (only formatting)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac834646b499`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.