# Issue

**Title:** Update RAG embedding model filter tag to 'vector-rag'

## Description

The `huggingface` data table now uses `vector-rag` as the `free_tag` for RAG embedding models instead of `embedding`.

Ref: usegalaxy-eu/infrastructure-playbook#2020

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c90b17006cc5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.