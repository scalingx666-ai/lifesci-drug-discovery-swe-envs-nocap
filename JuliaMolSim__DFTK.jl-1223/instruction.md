# Issue

**Title:** Screened Coulomb and range-separated hybrid functionals

## Description

I am opening this to discuss a new attempt for exact exchange in DFTK.  The code is not extensively tested but I want to see if this is the right direction and style.

Changes:
* implementation of exact exchange based on the exact-exchange branch by @mfherbst.
* includes various strategies to sample the Coulomb potential: spherical truncation, Wigner-Seitz truncation, probe charge Ewald.
* adding the option to display the convergence of the LOBPCG eigensolver.

Next steps:
* speed up application of Fock through adaptively compressed exchange (ACE) technique
* parallelization (maybe GPU?)

Comments:
* currently Gamma-only and non-spin polarized.
* maybe we have to look at the solvers. Currently small isolated molecules in large boxes fail to converge.
* enable hybrid functionals like PBE0 (as already implemented but I somehow messed it up)

Example:
```julia
model  = model_HF(lattice, atoms, positions; coulomb_model=WignerSeitzTruncated())
basis  = PlaneWaveBasis(model; Ecut=Ecut, kgrid=[1, 1, 1])
scfres_hf = self_consistent_field(
                basis;
                tol=1e-7,
                solver=DFTK.scf_damping_solver(damping=0.5), # isolated molecules converge better with 0.5
                ρ=scfres_pbe.ρ, 
                ψ=scfres_pbe.ψ, 
                maxiter=100, 
                diagtolalg=DFTK.AdaptiveDiagtol(; ratio_ρdiff=1e-5)
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `12c6ecf08cfb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.