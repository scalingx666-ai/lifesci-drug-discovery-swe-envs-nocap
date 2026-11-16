# Issue

**Title:** Refactor settings

## Description

Proceed with integrating rdkitJs.

### Changes

Introduce a parallel `reactionOptions` with the existing `options`, which is exactly the `moleculeOptions`. 06f35a8223aabafdec03bfac899b3dd2adbba5d9
Clean up settings initialization and migration. 06f35a8223aabafdec03bfac899b3dd2adbba5d9
Rename the `options` to `smilesDrawerOptions`. b0eb8996a64131e4e88ab657c0508f3e7feda500

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99cdbe977428`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.