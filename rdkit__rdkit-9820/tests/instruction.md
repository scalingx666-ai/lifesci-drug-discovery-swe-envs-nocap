# Issue

**Title:** Resolve embedding defaults before starting conformer workers

## Description

Fixes TSAN race in multithreaded embedder setup.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `15e2be3f352b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.