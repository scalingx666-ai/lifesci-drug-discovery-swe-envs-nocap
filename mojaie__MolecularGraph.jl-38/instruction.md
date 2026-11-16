# Issue

**Title:** Activate CI

## Description

I noticed in #37 that CI doesn't seem to run on pull requests. This is set to test Julia 1.3 (the earliest version you support), the latest stable release (currently Julia 1.5), and Julia nightly, allowing nightly to fail (because it often has temporary breakages).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90d6f6175f30`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.