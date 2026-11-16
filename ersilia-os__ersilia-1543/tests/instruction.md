# Issue

**Title:** Resolve duplication of values in CSV serialization

## Description

Fix csv serialization if input result is neither a dict nor a single value

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cca954b03b72`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.