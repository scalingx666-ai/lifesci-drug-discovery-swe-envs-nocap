# Issue

**Title:** Mordred: compute the spectral attributes of a stack of matrices at once

## Description

The thirteen spectral attributes were thirteen cached properties, each
reducing over the eigenvalues on its own, and every matrix was decomposed by
its own MatrixAttributes instance. They are now computed together by
spectral_attributes(), which takes a stack of matrices and returns an
(n_matrices, 13) array.

This matters most for the Barysz descriptors, which ask for the attributes of
eight matrices of the same molecule: the reductions run over arrays of a few
dozen numbers, where NumPy's dispatch costs more than the arithmetic, so doing
them once for the whole stack is what saves the time. MatrixAttributes stays
as the single-matrix front end, a stack of one.

- adjacency_matrix reuses the eigendecomposition the calculator now computes
  once, instead of decomposing the same matrix again
- adjacency_matrix and distance_matrix take AtomicProperties; barysz_matrix
  and detour_matrix pass theirs through to MatrixAttributes, their own bodies
  are untouched here

Values are unchanged except for VR1_Dt, VR2_Dt and VR3_Dt, which differ by up
to 4e-7 relative on 300 molecules sampled from MoleculeNet, TDC and
MoleculeACE - float32 rounding from summing the Randic-like terms in a
different order. Everything else is identical.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-03-graph-matrices` - review and merge in order.

<details>
<summary>The stack</summary>

1. #665 - feature names resolved per module
2. #666 - AtomicProperties
3. #667 - hydrogen-explicit matrices derived
4. #668 - spectral attributes over a stack  **<- this PR**
5. #669 - RingSets
6. #670 - subgraph enumeration (chi, path counts)
7. #671 - detour matrix
8. #672 - ETA descriptors
9. #673 - autocorrelations
10. #674 - Barysz matrices
11. #675 - E-state indices shared with VSA
12. #676 - BCUT (not computed before)
13. #677 - walk counts
14. #678 - conformer descriptors
15. #679 - atom, bond and constitutional counts
16. #680 - topological charge and Zagreb
17. #681 - ABC and molecular distance edge
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d85062f746e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.