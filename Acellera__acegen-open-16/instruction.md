# Issue

**Title:** add tokenizers

## Description

Added tokenizers to /vocabulary/tokenizers.py.

Each tokenizer can add and remove specified start/end tokens for functionality, but by default this is turned off as it is handled by the Vocabulary class.

Added default tokenizers to priors in main scripts, but nothing is done with the tokenizers yet ...

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9f3ee6da44bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.