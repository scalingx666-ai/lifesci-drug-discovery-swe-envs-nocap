# Issue

**Title:** Improve calc quality analysis implementation

## Description

## Changes / Fixes

1. Make the quality analysis also possible with CompleteDos objects as inputs (Should also allow us to bypass the Vasprun object serialization limitation for this  PR )
2. Dynamically determine the n_bins value based on input DOS data if the user-supplied n_bins is larger than the minimum number of data points available in specified energy interval

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `85f9dcb3d87f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.