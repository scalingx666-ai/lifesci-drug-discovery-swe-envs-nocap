# Issue

**Title:** Fix density mixing inconsitencies with MPI

## Description

This PR fixes MPI issues that became apparent with #1248.

The iterative `linsolve` solver from KrylovKit can output results that are numerically slightly different across MPI ranks. As a result, the density changes from rank to rank after `χ0Mixing` takes place.

Consequently, the SCF may need more iterations to reach convergence. This is usually not caught by the tests, as convergence is eventually reached anyways.

For response calculations, the consequences are more visible. Indeed, the input tolerance of the `solve_ΩplusK_split` solver [depends on Δρ](https://github.com/JuliaMolSim/DFTK.jl/blob/59fdee168f5a0510fce8f9da5a429f2e11225888/src/workarounds/forwarddiff_rules.jl#L262-L263). Therefore, the MPI ranks may leave `inexact_gmres` at different times, leading to a MPI breakdown.

**Note:** imposing a very tight tolerance to `linsolve` also seems to solve the problem, but I am worried about the cost.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `59fdee168f5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.