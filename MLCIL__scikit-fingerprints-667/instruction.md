# Issue

**Title:** Mordred: derive the hydrogen-explicit matrices instead of recomputing them

## Description

The distance matrix of the hydrogen-explicit molecule was computed from
scratch, an all-pairs shortest path over a molecule several times the size of
the heavy-atom one. Added hydrogens are terminal atoms, so their distances
follow from the heavy-atom distances: one bond to the atom a hydrogen hangs
off, and one at each end between two hydrogens.

- DistanceMatrix now wraps a matrix, built either by from_mol() or by
  with_hydrogens_added() from the heavy-atom distances
- eccentricities, radius and diameter are computed once in the constructor
  rather than on every property access
- RDKit's distance matrix cache is keyed per flag combination, so that the
  bond-order and atom-weight variants no longer evict each other
- the calculator derives the hydrogen-explicit molecule with AddHs(mol_regular)
  and its properties with AtomicProperties.with_hydrogens_added()

Output is unchanged: identical values on 300 molecules sampled from
MoleculeNet, TDC and MoleculeACE.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-02-atomic-properties` - review and merge in order.

<details>
<summary>The stack</summary>

1. #665 - feature names resolved per module
2. #666 - AtomicProperties
3. #667 - hydrogen-explicit matrices derived  **<- this PR**
4. #668 - spectral attributes over a stack
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e2e748046a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.