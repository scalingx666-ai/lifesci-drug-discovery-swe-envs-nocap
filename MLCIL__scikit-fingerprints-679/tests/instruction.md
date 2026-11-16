# Issue

**Title:** Mordred: count atoms, bonds and constitutional sums over arrays

## Description

Three descriptors that walked the molecule to count things now read the
shared property arrays:

- atom_count histograms the atomic numbers with bincount, instead of building
  a Counter and looking up each element of interest
- bond_count masks the bond type array, and takes the kekulized bond types
  that the calculator already extracts for the ETA descriptors, counting the
  hydrogen bonds as single, so it no longer reads the kekulized
  hydrogen-explicit molecule (still built for the ETA and information content
  descriptors)
- constitutional sums the per-atom property arrays directly

PROPERTY_FUNCS, kept while these descriptors still read one property of one
atom at a time, has no consumers left and is removed.

Output is unchanged: identical values on 300 molecules sampled from
MoleculeNet, TDC and MoleculeACE.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-14-3d` - review and merge in order.

<details>
<summary>The stack</summary>

1. #665 - feature names resolved per module
2. #666 - AtomicProperties
3. #667 - hydrogen-explicit matrices derived
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
15. #679 - atom, bond and constitutional counts  **<- this PR**
16. #680 - topological charge and Zagreb
17. #681 - ABC and molecular distance edge
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bac54d24cabc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.