# Issue

**Title:** CUDA build updates

## Description

This PR updates the build systems for recent CUDA versions (12.3).

Also, build options for injecting compilation flags for developer profiling were added for convenience.

 and #311.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `436148de8501`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.