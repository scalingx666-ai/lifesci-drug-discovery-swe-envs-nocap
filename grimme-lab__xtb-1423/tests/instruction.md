# Issue

**Title:** Fix rotational mode detection for diatomics

## Description

The `detrotra4/8` routines would score any mode with an eigenvalue below 0.05 to determine how well they preserved atomic distances, in order to classify low modes as translations/rotations vs vibrations. It would then sort these modes by score using the `ind` array and zero out the Hessian eigenvalues for the 6 (5 if linear) lowest scoring modes. 

This generally works fine, but if there aren't enough modes with an eigenvalue below 0.05, it would still try to zero out 5/6 modes even though some of the entries in `ind` would be undefined, leading to potential out of bounds access.

To avoid this, we check the number of low eigenvalue modes up front. If it isn't at least 5/6, we then check all the modes which should ensure we find 5/6 to remove. Checking all the modes shouldn't hurt performance, as we should only have this few small eigenvalues for small molecules, namely the diatomic case where a single value over the arbitrary 0.05 threshold was enough to cause a segfault.

-----

Beyond the bug fix, I also consolidated the interfaces for `detrota4/8` and have them use a common worker routine, since they perform the same algorithm just with single/double precision arrays.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b31754bf3c7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.