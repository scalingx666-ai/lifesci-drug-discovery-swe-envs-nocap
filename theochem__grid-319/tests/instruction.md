# Issue

**Title:** feat: add solve_poisson_robust (Split 1) and tests

## Description

@marco-2023 @PaulWAyers 
This PR implements `solve_poisson_robust()` in `src/grid/robust_poisson.py`, introducing the Split-1-Plus-Solve pipeline for a more robust electrostatic potential calculation. Related to #288. The solver improves on the plain `solve_poisson_bvp()` by pre subtracting the sharp nuclear core density before passing the residual to the BVP solver.

Pipeline:

    Total density rho(r)
          |
    [SPLIT 1]  load pre-fitted Gaussian params via load_atomic_gaussian_params()
          |     subtract core density → smooth, residual
          |
    [SOLVE]    solve_poisson_bvp on residual → phi_numerical
          |
    Total Potential = phi_core (analytical) + phi_numerical


No new external dependencies introduced.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `11bc98d8e857`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.