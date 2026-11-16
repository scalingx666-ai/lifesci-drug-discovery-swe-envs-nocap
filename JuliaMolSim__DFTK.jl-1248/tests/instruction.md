# Issue

**Title:** Extend MPI tests to ForwardDiff

## Description

The response code just works with MPI, and all ForwardDiff tests pass when run in parallel. To me, there is no good reason not to run these tests when testing with MPI.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93757d028995`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.