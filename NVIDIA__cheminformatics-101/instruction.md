# Issue

**Title:** NeMo Megamolbart checkpoint loading

## Description

@rilango This is a branch freshly created from dev that has most of what's needed to get checkpoint loading working in the inference.py file. There are a couple notes for you in `Dockerfile.megamolbart` and `inference.py` -- search for "TODO RAJESH".

Please feel free to pickup and use this branch directly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4da0e4e38c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.