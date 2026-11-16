# Issue

**Title:** Compile models to TorchScript

## Description

Models are refactored in a hierarchical manner so that `forward()` has a specific return type (instead of a flexible return type depending on the `affinity` flag.

This allows the compilation of all models into TorchScript. 

From some small test performed, it is not clear if compilation to TorchScript provides a good speedup.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2e4457ffca31`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.