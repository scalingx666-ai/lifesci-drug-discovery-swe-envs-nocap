# Issue

**Title:** Fix the k-point set used by the term-wise force test

## Description

`test_term_forces` built the displaced model with `symmetries=true`, which re-detects symmetries for the displaced positions. Displacing one atom breaks them, so the displaced basis can have more irreducible k-points than the `scfres.ψ` handed to `ene_ops`. On `GeO2_stretched` at `kgrid=[6,6,9]` that is 324 against 180: `ene_ops` iterates `enumerate(ψ)`, so it summed `kweights[1:180]` = 0.556 instead of 1, and the finite difference became the derivative of something that is not the nonlocal energy — off by ~0.7 against `compute_forces`.

`compute_forces` differentiates the energy summed over the *undisplaced* irreducible k-points, so the finite difference has to use those.

**Why this was never caught:** the affected item, `Forces term-wise Rutile (full)`, is `tags=[:slow,:forces]`, and no CI payload runs `:slow` — `minimal`/`example` restrict to their own tags, `nominimal-noslow` and `noslow-mpi` exclude `:slow`. It has been in this state since it was added in #1080. The other term-wise items are unaffected because `tio2_stretched` already has no symmetries, so the k-point count cannot change.

Verified on `GeO2_stretched` at `Ecut=20`, `kgrid=[2,2,3]` (where the same 8-vs-12 mismatch occurs), displacing each of the six atoms in turn:

| atom | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| before | 0.023 | 0.019 | 0.071 | 0.380 | 0.547 | 0.125 |
| after | 1.7e-10 | 1.1e-10 | 1.6e-8 | 2.9e-8 | 2.5e-8 | 1.1e-8 |

The residual is the `ε=1e-5` central-difference truncation error.

Also adds `@assert length(ψ) == length(basis.kpoints)` to the two `ene_ops` that loop over `ψ` rather than `basis.kpoints` (kinetic, nonlocal) — the silent truncation is what made this expensive to find. The other ψ-consuming terms index `ψ[ik]` from a basis loop and would already `BoundsError`.

Unrelated one-liner: `using DFTK` in the Fe term-wise item, so it runs under a bare `TestItemRunner.run_tests` and not only via `@run_package_tests` (which injects the import).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0592729c2fd1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.