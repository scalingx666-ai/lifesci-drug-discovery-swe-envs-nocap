# Issue

**Title:** Per-layer ffn hidden dims

## Description

> [!NOTE]
> This PR was handled entirely by Qwen 3.6 27b running locally via `opencode` with @JacksonBurns' supervision

Implements #1361 

~~Must be merged after #1367 (or merged into there)~~ undid this requirement in 228f5ee

## Checklist
- [x] linted with flake8?
- [x] (if appropriate) unit tests added?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `681e1ff76f28`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.