# Issue

**Title:** Defer GPU gradient annotations to fix test collection

## Description

The `gpu-cuda13-torch213` job failed during pytest collection because GPU gradient annotations referenced `SkalaRKS` and `SkalaUKS`, which are imported only for type checking.

- **Change:** Enable postponed annotation evaluation in `skala.gpu4pyscf.gradients`, preventing those type-only references from raising `NameError` during import.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1729a5015e7d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.