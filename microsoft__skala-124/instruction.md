# Issue

**Title:** add more instrumentation for gpu tests

## Description

We still have gpu tests failures because of memory corruption, we have not seen them in production code yet.

I am still not sure what the reason is, my hunch is that these come from some test setups, but to investigate further I want to add some more instrumentation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b2a66264fbd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.