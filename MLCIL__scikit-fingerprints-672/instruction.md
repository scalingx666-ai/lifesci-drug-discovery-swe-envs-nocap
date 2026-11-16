# Issue

**Title:** Mordred: compute the ETA descriptors over property arrays

## Description

The extended topochemical atom descriptors walked the kekulized molecule atom
by atom and bond by bond, building per-atom alpha and epsilon values in Python
loops, and asked for two molecules of their own: a kekulized copy and a
kekulized hydrogen-explicit copy, each with its own distance matrix.

Kekulization changes neither the atoms nor the skeleton, so the properties and
the distances of the hydrogen-suppressed molecule apply to the kekulized one
as well. The descriptor now takes those, plus the kekulized bond types as a
plain array, and computes the alpha and epsilon values as array operations.

- the kekulized copy is made from mol_regular rather than re-preprocessed from
  the input, so its atom numbering matches props_regular
- the separate kekulized distance matrix and the extra SSSR call are gone; the
  ring count comes from the shared RingSets
- PERIOD, kept as an alias while this descriptor still read the period one
  atom at a time, is removed

The 17 ETA columns that touch these sums differ by at most 3e-5 absolute
(1.2e-5 relative) on 300 molecules sampled from MoleculeNet, TDC and
MoleculeACE, from float32 accumulation order. The rest are identical.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-07-detour-matrix` - review and merge in order.

<details>
<summary>The stack</summary>

1. #665 - feature names resolved per module
2. #666 - AtomicProperties
3. #667 - hydrogen-explicit matrices derived
4. #668 - spectral attributes over a stack
5. #669 - RingSets
6. #670 - subgraph enumeration (chi, path counts)
7. #671 - detour matrix
8. #672 - ETA descriptors  **<- this PR**
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `90a59cfd9d40`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.