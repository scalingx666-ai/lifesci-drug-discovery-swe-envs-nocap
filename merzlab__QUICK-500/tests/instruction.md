# Issue

**Title:** Add code to approximate SAD density with idempotent density.

## Description

## Changes
* Recompute the density after overlap matrix is constructed in `getEnergy`
* Add new keyword `SADMO` that enables SAD idempotency correction
* Add new subroutine `lowdin_orth` to compute $S^{1/2}PS^{1/2}$

## The Method
1. Lowdin orthogonalize the density: $P'\coloneqq S^{1/2}PS^{1/2}$
2. Diagonalize $P'=C_\text{NO}'\Lambda{C_\text{NO}'}^\dagger$
3. Transform back to AO basis: $C_\text{NO}=S^{-1/2}C_\text{NO}'$
4. Set $\Lambda\mapsto N=\mathrm{diag}(1,\dotsc,1,0,\dotsc,0)$ and set $P\mapsto C_\text{NO}NC_\text{NO}^\dagger$

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2cb6a3b2cf6a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.