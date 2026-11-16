# Issue

**Title:** Add Aryl halides TL regression benchmarks

## Description

New aryl halides TL regression benchmarks based on the existing TL convergence benchmarks (reusing data loading, search space creation and number of MC iterations).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1010fe443ccf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.