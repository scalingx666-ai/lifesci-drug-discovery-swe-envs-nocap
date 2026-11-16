# Issue

**Title:** Spherical average

## Description

This pull request adds the spherical average of a function in AtomGrid class.  It returns a splines that takes in radial points.

The tests that are included are:
- The spherical average of a Gaussian is itself and its integral (with 4 pi r^2) of the spherical average function is the integral of the Gaussian (pi^1.5)
- The spherical average of a Spherical Harmonic (whose degree is less than the degree of the atom grid) is zero.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c83c9cd7f585`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.