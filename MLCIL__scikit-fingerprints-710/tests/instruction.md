# Issue

**Title:** Mordred cpsa sasa SR improvement

## Description

## Changes

CPSA surface areas now use Mordred's van der Waals radii instead of RDKit's. They still come from FreeSASA's Shrake-Rupley, the algorithm Mordred itself uses.

- **Radii**: `solvent_accessible_surface_area` reads Mordred's radii table (`periodic_table.VAN_DER_WAALS_RADII`). RDKit's radii were the main source of disagreement with Mordred; for example H is 1.20 Å in RDKit and 1.10 Å in Mordred, and N is 1.60 Å against 1.55 Å. The RDKit radii table `VAN_DER_WAALS_RADII_RDKIT` is removed, since nothing else used it.
- **Atoms without a radius**: Mordred's table has no radius for dummy atoms or for elements from 104 on. As in Mordred, such an atom gets a NaN area and covers no other atom, so CPSA values that don't sum over it stay finite. Its NaN reach overlaps nothing, so the existing lone-atom guard already leaves it out of `CalcSASA`.
- **Lone-atom guard**: kept as is. FreeSASA's Shrake-Rupley reads an atom's first neighbour without checking that it has one, so an atom that touches no other atom crashes or comes out wrong.
- **Stacked atoms**: two atoms of the same radius at the same position, as when fragments are embedded on top of each other, need no special handling. Shrake-Rupley returns finite areas made of rounding noise, as Mordred does.
- **Tests**:
  - SASA reference tolerance goes from 5% to 6%. FreeSASA uses 100 test points per atom where Mordred uses about 2,500, which reads totals up to about 6% low.
  - CPSA stays at 5%. RNCS and RPCS stay xfail because they depend on the area of a single atom.
  - New tests: an empty molecule, an atom without a radius (dummy atom and element 104), a molecule where no atom has a radius, a smaller atom inside a larger one, and stacked atoms.

### Accuracy against original Mordred

CPSA only, `n_jobs=-1`, 8 cores. "Within 5%" is the share of values within 5% of Mordred. RNCS and RPCS are excluded.

| Dataset | Molecules | Before (RDKit radii) | This PR | Mordred time | skfp time (this PR) |
|---|---|---|---|---|---|
| MolPILE 100k subset | 98,978 | 34.6% (median error 8.50%) | 91.3% (median error 1.29%) | 451 s | 5.5 s |
| ExpansionRx-OpenADMET | 7,608 | 37.4% | 93.0% | 50.4 s | 0.6 s |
| ASAP-OpenADMET | 1,486 | 34.2% | 94.2% | 10.2 s | 0.1 s |

On MolPILE, every molecule with an atom that has no radius gets the same NaN pattern as in Mordred, and this PR adds no NaN of its own.

### Follow-up

The remaining gap comes from the number of Shrake-Rupley test points, which RDKit's `SASAOpts` doesn't expose: `CalcSASA` always uses FreeSASA's default of 100. Measured on the same MolPILE molecules with the standalone `freesasa` package:

| Shrake-Rupley points | SASA time per molecule | Within 5% | Median error |
|---|---|---|---|
| 100 (this PR) | 0.19 ms | 92.0% | 1.27% |
| 500 | 0.47 ms | 99.3% | 0.40% |
| 1,000 | 0.78 ms | 99.6% | 0.28% |
| Lee-Richards, 20 slices (for comparison) | 0.72 ms | 99.4% | 0.32% |

I plan to open an RDKit PR exposing the point count. Once a release with it becomes skfp's minimum supported RDKit, 500 points would bring CPSA close to Mordred at little extra cost.

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes
- [x] Tests added, reasonable test coverage (at least ~90%, `make test-coverage`)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `383b87c4ab5a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.