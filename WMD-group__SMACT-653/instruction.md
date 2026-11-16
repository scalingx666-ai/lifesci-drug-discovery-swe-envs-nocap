# Issue

**Title:** docs: regenerate joss/paper.pdf from the current paper.md

## Description

The committed `joss/paper.pdf` was stale (last built in June), predating the pymatgen-comparison and dopant-prediction wording fixes merged in #646 for issue #642. Rebuilt it from the current `paper.md`/`paper.bib` via JOSS's own draft-PDF action, then dropped the one-off workflow used to build it — this is just the refreshed PDF, no other changes.

<!-- This is an auto-generated comment: release notes by coderabbit.ai -->

## Summary by CodeRabbit

* **Bug Fixes**
  * Prevented incompatible NVIDIA NCCL package combinations when installing the optional property prediction dependencies on Linux.
  * Restricted supported PyTorch versions to below 2.11 for improved compatibility.

<!-- end of auto-generated comment: release notes by coderabbit.ai -->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `97336357f0bf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.