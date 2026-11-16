# Issue

**Title:** nixpkgs: replace pinning source with channel sources

## Description

The channel source is smaller because it is packed with zstd instead of gzip.
This would also avoid GitHub rate limits.

I put this idea out here. We should test this a bit before merging to avoid unwanted surprises.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d3379a042937`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.