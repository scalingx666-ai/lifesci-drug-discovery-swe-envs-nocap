# Issue

**Title:** Fix random seed handling in simulation

## Description

Fixes a wrong assignment for controlling the random seeds in `simulate_scenarios`. Potentially, this was the cause for many weird effects noticed in the benchmarking module in the past.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `87301d4f9ffb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.