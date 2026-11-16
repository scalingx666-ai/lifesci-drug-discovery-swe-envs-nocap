# Issue

**Title:** Int changes

## Description

Rules for one dimension integration
    - Gauss Chebyshev 2
    - Gauss Chebyshev Lobatto
    - Trapezoidal
    - RectangleRules
    - TanhSinh
    - Simpson
    - MidPoint
    - ClenshawCurtis
    - FejerFirst
    - FejerSecond
    - Trefethen(ClenshawCurtis and GChebyshev2)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6cf3939e6706`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.