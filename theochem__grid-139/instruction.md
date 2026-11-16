# Issue

**Title:** Fix documentation domain issues in onedgrids

## Description

Small pull request that fixes the domain issues from [0, 1] to [-1, 1] for the RectangleRule and RectangleRuleEndpoints and replaced [-1:1] with [1, 1]

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `74a8e9c61e54`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.