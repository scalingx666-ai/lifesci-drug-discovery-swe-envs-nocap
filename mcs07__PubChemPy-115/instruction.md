# Issue

**Title:** Further refinement of new SMILES API

## Description

- Remove `absolute_smiles` property in favor of `smiles`
- Update docs, notebooks, tests to reflect changes to SMILES API.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4ab6270b04cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.