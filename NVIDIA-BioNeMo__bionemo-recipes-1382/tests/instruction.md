# Issue

**Title:** Refactor MLMDataCollatorWithFlattening

## Description

Updates this class to be more general for llama3 usage by making it accept a base collator and perform flattening after-the-fact. Essentially we're now always doing the bshd-compatable forward call.

This is going to make it easier to implement CP in the llama3 recipe

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7caf18c04f72`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.