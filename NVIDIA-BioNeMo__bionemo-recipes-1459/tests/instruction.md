# Issue

**Title:** make sure that we turn off quantized_model_init for llama3 lm_head

## Description

Fixes a strange bug where llama3 weights weren't tied and we used `quantized_model_init`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `79ca3bd8ef96`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.