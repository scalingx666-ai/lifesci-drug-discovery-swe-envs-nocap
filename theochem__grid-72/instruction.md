# Issue

**Title:** Make MolGrid weights consistent with Grid class

## Description

1. This makes weight attr contain the total integration weight.
2. MolGrid can now use integrate method of Grid class.
3. AtomicGrid weights are still stored in _atweights attr.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f1e4b60d5474`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.