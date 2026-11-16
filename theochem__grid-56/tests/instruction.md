# Issue

**Title:** Modifications of GaussLaguerre and GaussChebyshev functions

## Description

I wrote some modifications in onedgrid and test_onedgrid so that these functions return a grid which is suited to approximate the integral of f(x) and not f(x)*w(x) where w(x) is the weight function associated to the quadrature (x^alpha * e^(-x) for Gauss Laguerre and 1/sqrt(1 - x^2) for Gauss Chebyshev).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9a178509c80d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.