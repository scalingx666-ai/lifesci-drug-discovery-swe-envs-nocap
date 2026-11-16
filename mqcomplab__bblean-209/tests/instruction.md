# Issue

**Title:** Extract Common C++ Functions and add NEON SIMD support

## Description

Functions are extracted to a common location so that they can be used later in the optional full-C++ tree. The move can be viewed separately from the followup work via looking at the commit diffs.

Also makes some explicit alignment/padding changes to ensure vectorization.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `58981562528d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.