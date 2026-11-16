# Issue

**Title:** add stop+go tests to llama3 recipe, turn off async checkpointing for fp8

## Description

async dcp checkpointing is currently not working with fp8 model init, so we need to detect this and switch back to synchronous checkpointing. This also adds tests to ensure the dcp checkpoints are functional

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `493fb3f1feba`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.