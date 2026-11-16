# Issue

**Title:** Fix Hubbard symmetrization

## Description

## Problem
With a `Hubbard` term and symmetries, `symmetrize_hubbard_n` (`src/symmetry.jl`) was using wrong equation. It affects only if a symmetry orbit of Hubbard atoms has $`g\cdot a \ne g^{-1}\cdot a`$ for some symmetry $`g`$, e.g. three equivalent atoms cycled by a $`C_3`$ axis.

Example: Ni + 3 O in a hexagonal cell, U on O 2P.

| branch | symmetries | U = 0 | U = 0.3 |
|---|---|---|---|
| master  | false | -203.93848647698064 | -203.56772255059684 |
| master  | true  | -203.93848647698252 | **-203.472046798323** |
| this PR | false | -203.93848647698266 | -203.56772255059673 |
| this PR | true  | -203.9384864769806  | -203.56772255059343 |

<details><summary>MWE code</summary>

```julia
using DFTK
using PseudoPotentialData

family = PseudoFamily("dojo.nc.sr.pbe.v0_4_1.standard.upf")
Ni = ElementPsp(:Ni, family)
O  = ElementPsp(:O,  family)
lattice   = [7.0 -3.5 0; 0 3.5*sqrt(3) 0; 0 0 6.0]
positions = [[0.0, 0, 0], [0.2, 0.05, 0.15], [-0.05, 0.15, 0.15], [-0.15, -0.2, 0.15]]

function scf_energy(U; symmetries)
    hubbard = Hubbard(OrbitalManifold(:O, "2P") => U)
    model = model_DFT(lattice, [Ni, O, O, O], positions; functionals=LDA(),
                      extra_terms=[hubbard], temperature=1e-2, symmetries)
    basis = PlaneWaveBasis(model; Ecut=20, kgrid=[2, 2, 1])
    scfres = self_consistent_field(basis; tol=1e-10, callback=identity)
    scfres.energies.total
end

for U in (0.0, 0.3)
    E_nosym = scf_energy(U; symmetries=false)
    E_sym = scf_energy(U; symmetries=true)
    println("U = $U")
    println("E_nosym = $E_nosym")
    println("E_sym   = $E_sym")
end
```

</details>

## Fix
`src/symmetry.jl`, `symmetrize_hubbard_n`:

```diff
-            ns[σ, iatom, iatom] .+= WigD' * hubbard_n[σ, sym_atom, sym_atom] * WigD
+            ns[σ, iatom, iatom] .+= WigD * hubbard_n[σ, sym_atom, sym_atom] * WigD'
```

## Derivation of the symmetry transformation
In Cartesian coordinates a symmetry $`g`$ acts as $`gx = Wx + w`$, with $`W`$ orthogonal (`Wcart` in the code), and maps atom $`b`$ to atom $`g\cdot b`$ at $`r_{g\cdot b} = W r_b + w`$ (modulo a lattice vector). It acts on functions as $`(U_g f)(x) = f(g^{-1}x)`$, where $`g^{-1}x = W^T(x - w)`$. `wigner_d_matrix(l, Wcart)` returns the real matrix $`D_g`$ defined by $`Y(Wx) = D_g Y(x)`$, where $`Y = (Y_{l,-l}, \dots, Y_{l,l})`$ are the real spherical harmonics. Hence $`D_{gh} = D_g D_h`$ and $`D_g^T = D_{g^{-1}}`$, so $`Y_m(W^T y) = \sum_{m'} (D_g)_{m'm} Y_{m'}(y)`$.

For the orbital $`\varphi_{b,m}(x) = R(|x - r_b|) Y_m(x - r_b)`$, we have

```math
g^{-1}x - r_b = W^T(x - w - W r_b) = W^T(x - r_{g\cdot b}),
```

```math
(U_g \varphi_{b,m})(x) = R(|g^{-1}x - r_b|) Y_m(g^{-1}x - r_b) = R(|x - r_{g\cdot b}|) Y_m\bigl(W^T(x - r_{g\cdot b})\bigr) = \sum_{m'} \varphi_{g\cdot b,m'}(x) (D_g)_{m'm} .
```

With the orbitals of atom $`b`$ as a row vector $`\Phi_b = (\varphi_{b,-l}, \dots, \varphi_{b,l})`$, this reads $`U_g \Phi_b = \Phi_{g\cdot b} D_g`$, i.e. $`\Phi_{g\cdot b} = U_g \Phi_b D_g^T`$. The occupation matrix is $`n_b = \Phi_b^\dagger \hat\rho \Phi_b`$, i.e. $`n_b[m_1, m_2] = \langle \varphi_{b,m_1} | \hat\rho | \varphi_{b,m_2} \rangle`$. For a symmetric density matrix, $`U_g^\dagger \hat\rho U_g = \hat\rho`$, and since $`D_g`$ is real,

```math
n_{g\cdot b} = (U_g \Phi_b D_g^T)^\dagger \hat\rho (U_g \Phi_b D_g^T) = D_g \Phi_b^\dagger U_g^\dagger \hat\rho U_g \Phi_b D_g^T = D_g n_b D_g^T .
```

### Symmetrization
`find_symmetry_preimage` returns $`g^{-1}\cdot a`$, so the symmetrized occupation is

```math
N_a = \frac{1}{|G|} \sum_g D_g n_{g^{-1}\cdot a} D_g^T ,
```

while `master` computes $`\frac{1}{|G|} \sum_g D_g^T n_{g^{-1}\cdot a} D_g`$.

Existing tests were not seeing this because all test cases had $`g\cdot a = g^{-1}\cdot a`$ for all $`g`$ (orbits of one or two atoms).

## Test
New test item "Hubbard occupation symmetrization on a three-atom orbit" in `test/hubbard.jl`: $`C_3`$ symmetry (3 O, U on O 2P, `Ecut=10`, `kgrid=[2, 2, 1]`, SCF `tol=1e-6`). It checks that the SCF energy with symmetries equals the one without, to `atol=5e-6`:

| branch | $`E_\mathrm{sym} - E_\mathrm{nosym}`$ (Ha) |
|---|---|
| master | **1.2e-3** |
| this PR | 3.8e-8 |


Claude Code discovered the bug. I also used it to make changes and test. I reviewed and revised the output.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b80a6d1e01be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.