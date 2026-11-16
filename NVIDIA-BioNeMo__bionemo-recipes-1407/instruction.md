# Issue

**Title:** Add CP support to modeling_llama_te.py

## Description

* Makes the attention_mask type more easily controllable through a config kwarg
* passes the additional `_padded` kwargs through to the TE layers
* simplifies some of the pre-processing logic and adds comments as to why they're needed

Fixes BIO-12

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bb4421db85a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.