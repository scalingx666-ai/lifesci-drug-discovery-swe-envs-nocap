# Issue

**Title:** docs: update readme and types to reflect alternate wasm loading path

## Description

For some servers, the loading script will not be in the same location as the WASM module file.

Update documentation and types to reflect how to load rdkit-js from an alternate path.

Additional context from this discussion: https://github.com/rdkit/rdkit-js/discussions/360#discussioncomment-6478625

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6f5d62a2b5ee`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.