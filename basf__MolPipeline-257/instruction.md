# Issue

**Title:** replace default StandardScaler instance with Literal

## Description

This fixes the bug that all instances of a MolToDescriptorPipelineElement type share the same scaler instance.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `906fd38c8d13`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.