# Issue

**Title:** Proper error message for `strategy.predict`

## Description

Raise a proper error message when calling `strategy.predict` but no `self.experiments` are available. They are needed for the desirabilities.

cc: @jkeupp

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `748fd9ee6da8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.