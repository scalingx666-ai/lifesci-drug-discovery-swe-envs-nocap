# Issue

**Title:** Restrict fixing/constraints in ONIOM to whole system low level region

## Description

Apply fixed-atom settings, constraining potentials, walls and metadynamics biases only in the whole-system low-level ONIOM calculation, where atom numbering and reference geometries are consistent. Fixed-atom gradients are zeroed again after adding the inner-region correction.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3161bd2bcdf3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.