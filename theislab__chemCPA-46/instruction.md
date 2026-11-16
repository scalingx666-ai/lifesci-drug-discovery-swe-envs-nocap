# Issue

**Title:** Add rdkit embedding

## Description

Notebook and embedding is stored in `EMBEDDING_DIR/rdkit/`, paths are adjusted on embedding.py to include 200dim rdkit embeddings.

Adds to #29

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2598f591ed35`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.