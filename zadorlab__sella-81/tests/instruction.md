# Issue

**Title:** Fix guess Hessian projector, add exact_geodesic, revert rho_inc

## Description

Three fixes for quacc test regressions:

1. Use column-pivoting QR for guess Hessian projection. Non-pivoting QR keeps near-null-space directions (rigid-body modes with singular values at machine epsilon), leaking noise into the projected Hessian. Pivoting QR with rank truncation matches pinv to machine precision.

2. Add exact_geodesic option (default True) to recompute Binv at every ODE RHS evaluation, restoring pre-5edd166 accuracy for the geodesic integration. Users can set exact_geodesic=False for performance when the frozen Binv is sufficient.

3. Revert rho_inc for minimization from 4/3 back to 1.035. The wider window is beneficial for well-behaved potentials (pass rho_inc=4/3 explicitly), but can cause convergence failures with potentials that produce unreliable gradients for highly distorted geometries.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `64010d30e6a8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.