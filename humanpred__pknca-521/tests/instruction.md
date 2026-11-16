# Issue

**Title:** Add tmin (time of minimum concentration) parameter

## Description

Adds pk.calc.tmin() as the Tmin equivalent of pk.calc.tmax(), including a first.tmin option for tie-breaking, interval column registration, summary statistics, and full test coverage.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6f37b68cc840`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.