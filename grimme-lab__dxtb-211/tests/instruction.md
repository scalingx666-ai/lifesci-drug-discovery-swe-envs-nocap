# Issue

**Title:** Pydantic tensor serialization

## Description

- Allow tensors for all floats in the pydantic parametrization
- Serialize tensors from pydantic models
- Sync ordering between reference TOML file and written TOML files

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e86bc2543391`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.