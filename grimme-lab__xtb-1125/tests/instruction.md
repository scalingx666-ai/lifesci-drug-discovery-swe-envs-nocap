# Issue

**Title:** Fix optimization issues after #982

## Description

This patch fixes optimization issues comes from refactoring of geometry optimization done in #982.

I optimized some medium-size systems (~500-1500 atoms) and noticed that results between versions 6.7.0 and 6.7.1 are different. Moreover, geometry optimizations started to fail in 6.7.1 version, while it was OK for 6.7.0 version.

I found that problem comes from commit  in which the blowing up of hessian was moved.

I have tested this patch with a few iterations of my systems and it works almost like with 6.7.0 version.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3956a0e5d421`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.