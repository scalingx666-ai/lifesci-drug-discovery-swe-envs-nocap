# Issue

**Title:** Removing default fstep from readers

## Description

Removed defaults of 0.1ps fstep. Throws warning when fstep is 0 in metricdata

Taking care of issue:

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f5d002a6eca0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.