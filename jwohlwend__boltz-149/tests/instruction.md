# Issue

**Title:** Bug fix in Chunking

## Description

Fixes chunking code:
- The bias term from the output projection layer (`self.proj_o`) was not added.
- Also, the test for chunking did not set the layer to eval mode, so the chunking was not really tested before.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1ccc6b4c5d5c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.