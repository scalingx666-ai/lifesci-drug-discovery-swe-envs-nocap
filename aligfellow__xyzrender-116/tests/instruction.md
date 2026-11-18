# Issue

**Title:** Add manual ESP cmap range support and docs examples

## Description

Adds fixed-range ESP color mapping via --cmap-range / --cmap-symm. Addresses Issue #113 so users can compare ESP renders on a consistent scale.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9704ef28dd19`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.