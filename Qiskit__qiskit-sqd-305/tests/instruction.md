# Issue

**Title:** add fulqrum how-to guide

## Description

This is slower than the code in the fulqrum tutorial, but the main reason is that it's using the Python configuration recovery implementation. Once we switch that to the C++ version, the performance should be similar.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8e9916416c5f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.