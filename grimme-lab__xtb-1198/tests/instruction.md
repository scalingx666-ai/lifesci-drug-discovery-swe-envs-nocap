# Issue

**Title:** Possibility to skip the geometry optimizations during aISS docking

## Description

The final geometry optimizations during the aISS docking can now be skipped with the `--nfinal 0` flag.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65e9c14cd387`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.