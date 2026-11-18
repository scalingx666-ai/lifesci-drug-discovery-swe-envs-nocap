# Issue

**Title:** GPU LRI Build Fix with f Function Support

## Description

This PR addresses a build failure reported in #425 in the GPU LRI code with AmberTools when f function support is enabled.

Specifically, the vertical_spdf2 device function was accidentally omitted following the non-LRI & LRI VRR code split (see files `src/gpu/int.h` and `src/gpu/int_lri.h`, respectively).

Code in the PR will also need to be upstreamed to AmberTools 2025 as a point release to push out this fix to users.

.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e63c81dc2359`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.