# Issue

**Title:** Switch the pytorch integrals to the CCA orbital ordering of tblite

## Description

## Summary

Switches the pytorch integral drivers to the CCA orbital ordering that tblite adopted in tblite/tblite#371:

- Cartesian functions are now in lexicographic order (`xx, xy, xz, yy, yz, zz, ...`).
- Spherical components are now in ascending m (`-l, ..., l`) for d and f shells.
- p stays `y, z, x` (m = -1, 0, 1), as in tblite.

### ⚠️ Breaking change

The d components of every AO-resolved quantity from the pytorch drivers change order:

| | order of the d components |
|---|---|
| before | `z2, xz, yz, x2-y2, xy` (m = 0, +1, −1, +2, −2) |
| after | `xy, yz, z2, xz, x2-y2` (m = −2, …, +2) |

This affects the overlap, H0, the density and orbital coefficients. Energies, forces, charges and everything else that is invariant within a shell are unchanged. The libcint driver already returns d in this order, so the two drivers now differ only in p.

The f transformation was already correct (verified against PySCF). The FIXME saying otherwise is removed, and the matrix is rewritten in the new cartesian order. dxtb has no Molden/TREXIO writers, so nothing else depends on the order.

## Tests

- New `test_ao_ordering.py` compares every shell pair from s-s to f-f element-wise with PySCF at 1e-14, covering both order and signs. With the old order, 7 of its 16 cases fail: every pair that involves a d shell.
  - The test pins `pyscf.gto.mole.NORMALIZE_GTO = True`, because dxtb's PySCF interface sets it to `False` globally on import.
- The frozen references (`test_overlap/overlap.npz`, `test_hamiltonian/h0.npz`, and the inline 3d-3d/3d-4d references in `test_grad.py`) are **permuted**, not regenerated. They differ from the old references only by the reordering.
- `test_driver_precision.py`: the libcint permutation for d is now the identity.

Full suite (`-m "not large"`, in random order): 3212 passed, 12 xfailed.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `46af7bcdb53e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.