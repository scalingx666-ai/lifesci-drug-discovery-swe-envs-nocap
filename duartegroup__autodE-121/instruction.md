# Issue

**Title:** Add default low_sp keywords

## Description

Adds a default set of low-level single point keywords used if `ade.Config.hmethod_sp_conformers = True`. Suggested by Thijs – thanks for the suggestion 😄.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2c5e1ec51c33`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.