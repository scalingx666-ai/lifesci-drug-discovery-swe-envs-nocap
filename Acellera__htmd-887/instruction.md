# Issue

**Title:** Fixed bug in metricdata and model saving and loading

## Description

Reported by Cesar. Seems like at some point long ago I broke the save/load feature. Fixed it now and added tests so that it stays fixed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ecb92f893a6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.