# Issue

**Title:** CI fails again with un-descriptive conda error message

## Description

## Description
CI fails again with un-descriptive conda error message:
`Error: The process '/usr/share/miniconda/condabin/conda' failed with exit code 1`

See discussion here: 
-> Might be resolved by using `mambaforge` instead of mamba as resolver.

## Todos
- [x] CI: Update actions/checkout from v2 to v3
- [x] CI: Use mambaforge instead of mamba as resolver

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1b3c08b48ca5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.