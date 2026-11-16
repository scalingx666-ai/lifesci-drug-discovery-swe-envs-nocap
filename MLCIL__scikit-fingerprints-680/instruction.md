# Issue

**Title:** Mordred: accumulate the topological charge and Zagreb sums with bincount

## Description

- topological_charge bucketed the atom pairs by topological distance with one
  boolean mask per order, seven passes over the whole matrix; the orders are
  now accumulated in a single bincount over the distances, with the pairs it
  does not want mapped to a bucket that is dropped
- zagreb_index reads the degrees and the valence degrees from the shared
  properties, instead of summing over atoms and bonds in Python

Output is unchanged: identical values on 300 molecules sampled from
MoleculeNet, TDC and MoleculeACE.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-15-counts` - review and merge in order.

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
15. #679 - atom, bond and constitutional counts
16. #680 - topological charge and Zagreb  **<- this PR**
17. #681 - ABC and molecular distance edge
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cf51ef66e232`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.