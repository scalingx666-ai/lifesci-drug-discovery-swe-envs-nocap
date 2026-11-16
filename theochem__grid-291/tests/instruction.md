# Issue

**Title:** Fix spherical harmonics for new SciPy sph_harm_y API

## Description

Replace deprecated sph_harm with sph_harm_y and update argument ordering to match SciPy’s azimuth/polar convention. Ensure magnetic quantum numbers are always integers, and construct negative-m real harmonics from the imaginary part of positive-m modes.

Simplify HORTON-2 m ordering and fix derivative evaluation to avoid invalid float m values. This restores compatibility with SciPy ≥1.17 and fixes test failures.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `081c106085d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.