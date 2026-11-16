# Issue

**Title:** Parse directional dative bonds in SMI files

## Description

This repair is part of our study on testing chemical software repositories with scenario-specific, chemistry-aware invariants.

.

The branch contains a focused regression test for the reported chemical file-format behavior.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `582e6da1ce7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.