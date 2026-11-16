# Issue

**Title:** Update QCG settings with new ensemble generation

## Description

The new ensemble generation for QCG (`--qcgmtd`) is now set to be the default. It uses low-energy MDs and MTDs to generate new structures. The old ensemble generation can be invoked with `--ncimtd`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a5aa780205dd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.