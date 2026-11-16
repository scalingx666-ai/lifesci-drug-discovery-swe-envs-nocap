# Issue

**Title:** Fix template matched

## Description

User input chain_ids and template_chain_ids will never make matched=True.  Set matched = True when both are not empty and have the same length.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b1e17ed18516`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.