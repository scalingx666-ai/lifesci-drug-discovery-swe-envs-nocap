# Issue

**Title:** Code clean-up, CI update and add custom matplotlib stylesheet

## Description

Changes:
- Update pylintrc
- Added pre-commit check in CI
- Clarify `--no-expand` option in the documentation
- allow custom matplotlib stylesheet to be used in the CLI

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93e8a8e43828`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.