# Issue

**Title:** fix(ops): remove redundant CMS_INTERNAL_AUTH_TOKEN interpolation

## Description

Already loaded into the API container via env_file. The interpolation caused a warning because compose looks for .env in the compose file directory (ops/), not the project root.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fb714525f18a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.