# Issue

**Title:** Posterior transform for objectives

## Description

by properly handling Gaussianity-preserving (a.k.a. affine) transformations via a dedicated processing route utilizing BoTorch's `PosteriorTransformation`. Because the acquisition builder can now rely on this mechanism, much boilerplate could be removed from there (including the wrong logic causing #661) and be replaced with improved error handling instead.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e65f2c72f62d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.