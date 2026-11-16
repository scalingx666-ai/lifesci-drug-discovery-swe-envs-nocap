# Issue

**Title:** Fix differentiation of nonlocal projectors at p=0 by switching to solid harmonics

## Description

Spherical coordinates at p=0 are awkward, and this causes problems for AD wrt. k at G+k=0 for projectors that have angular momentum l=1: the derivative should not be zero, but our guards against small p make it 0. Additionally, only the product of the Hankel transform and the spherical harmonics is differentiable, but not each of them on their own.

The best fix I could find find (thanks Claude, although all the code is mine) was to move the `1/p^l` from the spherical harmonic to the Hankel transform. This gives a "regularized" Hankel transform (whose derivative is always 0 at p=0) times a solid harmonic. With this trick the derivative is $H(0) \cdot \partial_\alpha R_{lm}(0)$ which is always well-defined! And since $R_{lm}$ is a homogeneous polynomial of degree l this cleanly explains why only projectors at l=1 contribute to the derivative.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `38d2c2e906f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.