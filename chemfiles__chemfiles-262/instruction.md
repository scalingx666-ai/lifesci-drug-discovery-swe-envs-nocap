# Issue

**Title:** feat(XTC): replace Molfile with our own implementation

## Description

Use `xdrfile` to make use of offsets for `read_step`. Eliminates the large memory usage.
Ticks a box in #154.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a291902c2208`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.