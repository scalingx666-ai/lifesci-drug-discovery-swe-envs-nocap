# Issue

**Title:** Remove deprecated `force_consistent` parameter

## Description

(CC @samblau, @juditzador). This PR removes the `force_consistent: bool` parameter since the `force_consistent` parameter was deprecated in ASE and has now been removed. I can confirm that the minimal example in the sella README runs appropriately with this patch.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `37395fc75c2a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.