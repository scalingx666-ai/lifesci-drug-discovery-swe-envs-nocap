# Issue

**Title:** fix: optimize BertzCT calculation by using bond-order weighted distan…

## Description

…ce matrix

## Changes

BertzCT now gets the distance matrix it actually uses, and RDKit no longer recomputes it.

RDKit's `BertzCT` builds its atom symmetry classes from **bond-order weighted** distances (`useBO=True`). With the default `forceDMat=True` it ignores the `dMat` we pass and computes two matrices from scratch for every molecule: an unweighted one that it overwrites without using, and the weighted one. Mordred-community has the same waste (`BertzCT(mol, dMat=D)` with an unweighted `D` and no `forceDMat`). The values come out right only because the passed matrix is never read.

That is why `forceDMat=False` broke values when we tried it before. We were passing the unweighted matrix, so the symmetry classes changed (13,534 / 41,127 molecules differed on HIV). It is not an RDKit bug, and RDKit doesn't need both matrices.

- `calc_rdkit_2d` builds `DistanceMatrix.from_mol(mol_regular, use_bond_orders=True)` once (its own cache prefix, so it doesn't overwrite the unweighted one) and passes it to `BertzCT` with `forceDMat=False`. Per molecule that is 1 matrix instead of 2.
- A short comment above the call explains why BertzCT gets a different matrix than BalabanJ.
- BalabanJ is unchanged; it already uses the passed matrix (`forceDMat=0` by default).

**Results on MolPILE `molpile_subset_100k`**, old vs new `calc_rdkit_2d`, input preparation not timed, 2 runs:
- values: **100,000 / 100,000 molecules bit-identical**
- `calc_rdkit_2d` total: 43.0 s → 41.6 s (**−3%**); the gain grows with size: <20 heavy atoms ±0%, 20–39 −2%, 40–69 −6%, ≥70 **−13%**

## Checklist before requesting a review
- [x] Docstrings added/updated in public functions and classes (no public API changes; comment added at the call site)
- [x] Tests added, reasonable test coverage (no new behaviour to cover, since outputs are bit-identical; all `tests/fingerprints/_new_mordred` pass: 3643 passed, 104 skipped, 10 xfailed, 57 xpassed)
- [x] Sphinx docs added/updated and render properly (not applicable, no docs changes)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e3a68ae45ef`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.