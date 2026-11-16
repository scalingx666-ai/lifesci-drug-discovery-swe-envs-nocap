# Issue

**Title:** Update networkx version specification in setup.cfg

## Description

Update NX requirements to 3.x, which is needed because of the length_bound argument in simple_cycles.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `10a9ccd6cedb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.