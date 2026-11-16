# Issue

**Title:** Cgtos fixes

## Description

# cGTOs: fixes for complex-exponent Gaussian AOs + full-precision `pi_5_2`

Branch `cgtos-fixes` → `dev-stable` (2 commits, 7 files in `src/`, +157 / −44).

## ⚠ Change affecting standard (real-Gaussian) QP2 results

Commit `c3b039bd` sets `pi_5_2` (= 2π^{5/2}, `src/utils/constants.include.F`) to full double precision.
The old value `34.9868366552d0` had 12 significant digits only.

- **Every two-electron integral** changes by **+1.42e-12 relative**: Coulomb, erf/range-separated and cGTO
  integrals alike.
- Total energies shift by about 1.4e-12 × E_ee, e.g. ~7e-11 Ha for H2O.
- ERIs vs PySCF improve from 2.7e-12 to 1.5e-14 (relative).
- **A clean rebuild is required**, because ninja does not track `constants.include.F`: remove the
  `IRPF90_temp` directories before rebuilding.

This commit is separate from the cGTO fixes, so it can be reverted on its own.

## cGTO fixes (commit `fbb476bb`)

| # | file | problem | fix |
|---|---|---|---|
| 1 | `utils/cpx_erf.irp.f` | Boys function is **NaN on the negative real axis** and inaccurate near it. This is hit in practice: the same shell on two atoms gives T = −(b²/a)R² exactly. NaN ERIs were silently stored (H2, b/a = 2); at b/a = 5 one ERI was 634 instead of −0.004. | principal branch of the complex sqrt; remove the `x == 0` shortcut in `erf_G` |
| 2 | `utils/cpx_boys.irp.f` | series for 0.35 ≤ \|T\| < 3.5 stopped at an absolute 1e-10, giving Boys errors up to 6.5e-9 | relative tolerance 1e-17, `kmax` 100 |
| 3 | `utils/cgtos_utils.irp.f`, `ao_one_e_ints/one_e_coul_integrals_cgtos.irp.f` | screening on the prefactor \|K\| is **not a bound** with complex exponents (F_n(T) with Re T ≪ 0 compensates it). ERIs were wrong by up to 100%, V by 1.8%. | new `cgaussian_pair_bound` = exp(−a₁a₂/(a₁+a₂)\|A−B\|²) built from the real parts and the nuclear centres; no cut inside `cgaussian_product` |
| 4 | `ao_one_e_ints/one_e_coul_integrals_cgtos.irp.f` | nuclear attraction wrong when `ao_expo_pw ≠ 0`: the product centre was built from the polynomial centres instead of the complex Gaussian centres | pass the complex product centre P |
| 5 | `trexio/export_trexio_routines.irp.f` | `export_trexio` wrote the real Gaussian basis for a cGTO EZFIO, so AOs read back from TREXIO were wrong | export as TREXIO `oscillation_kind = "Cos2"` with `oscillation_arg = b`, `prim_factor = 2N` and the cGTO `ao_normalization`. No TREXIO format change is needed. |
| 6 | `ao_basis/cgtos.irp.f` | `ao_normalized` was ignored by the cGTO path; since `qp_create_ezfio` writes `ao_normalized = True`, cGTO AOs were left unnormalized (⟨χ\|χ⟩ down to 0.58) | the contraction normalization now honours `ao_normalized` |

**Behaviour change for existing cGTO EZFIOs (fix 6):** with `ao_normalized = True` the cGTO AOs are now
normalized, so stored MO coefficients refer to differently scaled AOs. Rerun SCF, or set
`ao_normalized = False` to keep the old definition. Real-Gaussian calculations are not affected.

## Validation

All results below are from this branch, rebuilt from scratch on top of the current `dev-stable`. They were
checked against an independent arbitrary-precision (mpmath) McMurchie–Davidson reference, PySCF, numerical
quadrature and Monte Carlo:

- **Integrals:** S, T, V and ERIs agree with the reference to 1e-14 – 1e-13 relative for 0 ≤ b/a ≤ 10 (H2,
  LiH, H2O, s–f shells, with and without plane-wave factors).
- **b → 0 limit:** cGTO, standard QP2 and PySCF agree to 1.5e-14.
- **Invariants:** 8-fold ERI symmetry, Schwarz inequality and a positive semidefinite ERI matrix all hold,
  with no NaN.
- **Energies:** variational bounds hold, Cholesky and direct ERIs give identical energies, and
  rotation/translation invariance holds to 1e-9 – 1e-8 (HF).
- **TREXIO:** AOs evaluated from the exported file match the reference to 9e-16. A matching QMCkl patch for
  `Cos2` exists; its PR will be proposed to the QMCkl developers.

The tests and reference scripts live outside the QP2 repository, in `qp_plugins_ammar/cgtos_validation`
(run with `run_all.sh --quick`).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a5a3fe0a87d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.