# Issue

**Title:** AWG Update runtest script for Amber

## Description

In Amber
- Assume this runtest script gets installed into $AMBERHOME/AmberTools/src/quick/
- While binaries are in $AMBERHOME/bin.

This update will make sure we find the binary folder. It also removes the Run.tests.amber script which is redundant and does not work as intended.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e7b73237022`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.