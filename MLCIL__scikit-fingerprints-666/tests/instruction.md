# Issue

**Title:** Mordred: read per-atom properties into arrays once per molecule

## Description

The descriptors each walked the molecule themselves, calling RDKit once per
atom or bond for the same quantities - atomic numbers, degrees, hydrogen
counts, valence electrons, Gasteiger charges. AtomicProperties reads them
into NumPy arrays once and hands the same arrays to every descriptor.

- AtomicProperties.from_mol() collects the per-atom and per-bond arrays, with
  the derived ones (valence electrons, intrinsic state, neighbor counts)
  computed lazily and cached
- with_hydrogens_added() builds the hydrogen-explicit properties from the
  heavy-atom ones instead of re-reading the molecule
- PeriodicTable.lookup() indexes a padded array with an atomic number vector,
  for whole-molecule lookups
- the calculator builds props_regular and props_hydrogens and passes them on

Four descriptors move to it here as the first consumers: aromatic,
fragment_complexity, polarizability and vertex_adjacency_info. The rest
follow one PR at a time; PROPERTY_FUNCS and PERIOD stay for now, since the
descriptors that have not moved yet still read a property at a time.

Output is unchanged: identical values on 300 molecules sampled from
MoleculeNet, TDC and MoleculeACE.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-01-feature-names` - review and merge in order.

<details>
<summary>The stack</summary>

1. #665 - feature names resolved per module
2. #666 - AtomicProperties  **<- this PR**
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
15. #679 - atom, bond and constitutional counts
16. #680 - topological charge and Zagreb
17. #681 - ABC and molecular distance edge
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `722a3c2872de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.