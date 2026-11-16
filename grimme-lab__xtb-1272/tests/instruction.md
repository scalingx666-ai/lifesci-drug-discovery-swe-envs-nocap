# Issue

**Title:** Small speed-up of gradient for non-PBC case

## Description

I have split PBC and non-PBC case in `atm_gradient_latp` subroutine that saves 30 ms for `0418_0016xGluAla.xyz` (418 atoms) and 300 ms for `0834_0032xGluAla.xyz` (834 atoms) per each geom.iter for 4 cores with ifx 2025.1. For larger number of atoms the effect should be larger.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09288659551c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.