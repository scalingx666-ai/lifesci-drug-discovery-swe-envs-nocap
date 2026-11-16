# Issue

**Title:** Mordred: build the eight Barysz matrices as one stack

## Description

The Barysz descriptors build a weighted distance matrix per atomic property,
eight in all, and take the spectral attributes of each. Every matrix was built
by walking the bonds in Python, and each was decomposed on its own.

The weights of all eight are now computed together as one array indexed by
bond and property, the matrices are filled as a stack, and their attributes
come from a single spectral_attributes() call over that stack.

Output is unchanged: identical values on 300 molecules sampled from
MoleculeNet, TDC and MoleculeACE.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-09-autocorrelation` - review and merge in order.

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
10. #674 - Barysz matrices  **<- this PR**
11. #675 - E-state indices shared with VSA
12. #676 - BCUT (not computed before)
13. #677 - walk counts
14. #678 - conformer descriptors
15. #679 - atom, bond and constitutional counts
16. #680 - topological charge and Zagreb
17. #681 - ABC and molecular distance edge
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98f1b7a29bfd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.