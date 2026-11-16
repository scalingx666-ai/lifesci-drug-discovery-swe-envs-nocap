# Issue

**Title:** Mordred: enumerate the connected subgraphs once, with array operations

## Description

The chi and path count descriptors each enumerated the connected subgraphs of
the molecule themselves, in Python, one subgraph at a time - together the
largest cost in the whole calculator, around 29% of its Python time. Subgraphs
enumerates them once per molecule: subgraphs of each order are grown from
those of the previous order by adding one adjacent bond, entirely with array
operations over flat index arrays.

- utils/subgraphs.py enumerates up to order 7, the largest the chi descriptors
  ask for, and classifies each subgraph as chain, path, path cluster or
  cluster
- the atom index sets of a type are gathered only when a descriptor asks for
  them, since chi wants different types at different orders
- utils/ragged.py holds the two helpers for rows of unequal length that this
  bookkeeping needs
- chi and path_count read the shared Subgraphs and the shared properties

Computing all 2D descriptors for 400 molecules drops from 19.5s to 8.5s.

Values are unchanged except for 54 chi columns (Xc, Xch, Xp, Xpc, AXp), which
differ by up to 3.4e-6 relative on 300 molecules sampled from MoleculeNet,
TDC and MoleculeACE - float32 rounding from summing the per-subgraph terms in
a different order.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-05-ring-sets` - review and merge in order.

<details>
<summary>The stack</summary>

1. #665 - feature names resolved per module
2. #666 - AtomicProperties
3. #667 - hydrogen-explicit matrices derived
4. #668 - spectral attributes over a stack
5. #669 - RingSets
6. #670 - subgraph enumeration (chi, path counts)  **<- this PR**
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f40681b47a4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.