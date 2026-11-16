# Issue

**Title:** Fix Auto-Zoom Bug

## Description

Previously, the algorithm for determining the initial zoom was just plain wrong. Thank you @scemama for noticing ( #13 )!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `53e30aa813ed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.