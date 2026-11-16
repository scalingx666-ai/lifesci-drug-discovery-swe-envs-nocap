# Issue

**Title:** Patch/beam central

## Description

Minor update to BEAM to support stereo on ``CN=C=NC`` e.g. ``CN=[C@AL1]=NC`` and ``CN=[C@AL2]=NC``.
I have also add the change here I needed to deploy snapshots.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `770b0fd3672f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.