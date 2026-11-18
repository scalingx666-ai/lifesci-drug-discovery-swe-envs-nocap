# Issue

**Title:** Revision t036 egnn

## Description

## Description
Handles the following reviewer comment

> Clarify E(3) invariance versus equivariance. The manuscript correctly introduces both concepts and explains that scalar properties should remain invariant under rigid rotations/translations. However, terminology varies between “EGNN,” “E(3)-invariant graph neural network,” and, in the presubmission letter, “SE(3)-equivariant neural networks.” The notation should be made consistent, and the distinction between an equivariant internal representation/layer and an invariant scalar prediction should be explicitly explained. The distinction between E(3) and SE(3), particularly treatment of reflections, could also be mentioned briefly.

Changes:
- Replaces confusing use of EGNN acronym by E(3)-invariant GNN.
- Clarified E3 vs SE3 and role of reflection for molecular ML.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f292c9a3897`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.