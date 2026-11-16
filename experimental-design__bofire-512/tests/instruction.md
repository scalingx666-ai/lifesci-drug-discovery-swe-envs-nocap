# Issue

**Title:** Fix failing doe notebooks

## Description

The doe basic examples often fail as pointed out by @jduerholt in #510. This PR avoids raising an error by setting  raise_validation_error=False in `ask()` for the cone examples to avoid raising errors due to slightly violated constraints.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e1261e1c8ef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.