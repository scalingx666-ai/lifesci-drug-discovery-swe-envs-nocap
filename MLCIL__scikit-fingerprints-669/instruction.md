# Issue

**Title:** Mordred: perceive the rings of a molecule once, in RingSets

## Description

Ring perception was repeated per descriptor: ring_count called GetSymmSSSR
and then walked every ring to check aromaticity and heteroatoms, and
vdw_volume_abc did the same work again through the private helpers of
ring_count. RingSets does it once per molecule, caching the simple and the
fused ring atom sets together with the size, aromaticity and heteroatom flags
of each ring.

- ring counts are read off boolean masks over the cached ring properties,
  rather than recomputing the predicates per ring size bucket
- vdw_volume_abc takes the shared RingSets and the hydrogen-explicit
  properties, and its Bondi volumes are a table indexed by atomic number
  instead of a dict keyed by element symbol
- the calculator builds rings_regular next to props_regular

Output is unchanged: identical values on 300 molecules sampled from
MoleculeNet, TDC and MoleculeACE.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-04-matrix-attributes` - review and merge in order.

<details>
<summary>The stack</summary>

1. #665 - feature names resolved per module
2. #666 - AtomicProperties
3. #667 - hydrogen-explicit matrices derived
4. #668 - spectral attributes over a stack
5. #669 - RingSets  **<- this PR**
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ec0bf8065847`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.