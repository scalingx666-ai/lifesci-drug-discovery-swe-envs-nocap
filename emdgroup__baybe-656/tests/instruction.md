# Issue

**Title:** Add generic parameters to `to_json()` method to be funneled to `json.dumps()`

## Description

This is e.g. useful to set `indent=2` for pretty-printing the JSON output.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2a2e48e9e34f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.