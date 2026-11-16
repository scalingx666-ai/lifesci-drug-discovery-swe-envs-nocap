# Issue

**Title:** Throw error if hubbard_n is not passed to TermHubbard

## Description

`ene_ops(::TermHubbard)` silently returns `E = 0` and a `NoopOperator` when no `hubbard_n` is passed. This affects routines that do not yet support DFT+U: they run but give a wrong result. For example, `direct_minimization` on a DFT+U model runs and returns the plain-DFT result.

## Fix
- `src/terms/hubbard.jl`: `ene_ops(::TermHubbard)` throws an `ArgumentError` when `hubbard_n` is missing, similarly as `TermXc` for MetaGGA does for a missing `τ`.
- `self_consistent_field` relied on `hubbard_n = nothing` (U = 0) for its first step. It now starts from `guess_hubbard_n` (cherry-picked from #1362): $`n = I/2`$, i.e. a zero Hubbard potential $`D = \frac{U}{2}(1 - 2n) = 0`$, so the first Hamiltonian is unchanged.

## Test
`test/hubbard.jl`: `ene_ops(::TermHubbard)` and `energy_hamiltonian` without `hubbard_n` throw an `ArgumentError`.

## MWE for silently wrong result

Silicon, U = 5 eV on Si 3P, LDA, `Ecut = 10`, 2×2×2 k-points, on `master` @ `b4d490e7`:

| run | `E_total` (Ha) | `E_Hubbard` (Ha) | $`\lVert\rho - \rho_\mathrm{SCF}(U)\rVert`$ | $`\lVert\rho - \rho_\mathrm{SCF}(\text{no } U)\rVert`$ |
|---|---|---|---|---|
| `self_consistent_field`, U = 5 eV | −8.1522125822 | 0.2754324317 | 0 | 4.2e-4 |
| `self_consistent_field`, no Hubbard term | −8.4276558241 | 0 | 4.2e-4 | 0 |
| **`direct_minimization`, U = 5 eV** | **−8.4276558241** | **0** | 4.2e-4 | **1.9e-10** |

<details><summary>MWE</summary>

```julia
# DFT+U silicon (U = 5 eV on Si 3P): direct_minimization vs self_consistent_field
using DFTK, PseudoPotentialData, LinearAlgebra

a = 10.26
lattice = a / 2 * [[0 1 1.]; [1 0 1.]; [1 1 0.]]
Si = ElementPsp(:Si, PseudoFamily("dojo.nc.sr.lda.v0_4_1.standard.upf"))
atoms = [Si, Si]
positions = [ones(3)/8, -ones(3)/8]
U = 5 / 27.211386245988  # 5 eV in Hartree

make_basis(extra_terms) = PlaneWaveBasis(model_DFT(lattice, atoms, positions; functionals=LDA(),
                                                   extra_terms); Ecut=10, kgrid=[2, 2, 2])
basis_U  = make_basis([Hubbard(OrbitalManifold(Si, "3P") => U)])
basis_0  = make_basis([])

scfres_U = self_consistent_field(basis_U; tol=1e-9, callback=identity)
scfres_0 = self_consistent_field(basis_0; tol=1e-9, callback=identity)
dm_U     = direct_minimization(basis_U; tol=1e-9, callback=identity)

dρ(r1, r2) = norm(r1.ρ - r2.ρ) * sqrt(basis_U.dvol)
for (name, r) in [("SCF, U = 5 eV", scfres_U), ("SCF, no Hubbard term", scfres_0),
                  ("direct_minimization, U = 5 eV", dm_U)]
    EH = haskey(r.energies, "Hubbard") ? r.energies["Hubbard"] : 0.0
    println(rpad(name, 30), "  E_total = ", r.energies.total, "  E_Hubbard = ", EH,
            "  |ρ - ρ_SCF(U)| = ", dρ(r, scfres_U), "  |ρ - ρ_SCF(no U)| = ", dρ(r, scfres_0))
end
```

</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4d490e7d2f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.