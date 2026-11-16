# Issue

**Title:** Mordred: take the walk counts from the adjacency spectrum

## Description

The walk counts multiplied the adjacency matrix by itself ten times, one dense
matrix product per order, to sum and trace each power. The same numbers follow
from the eigendecomposition the calculator already computes for the adjacency
descriptors: the k-th power has the same eigenvectors and the k-th powers of
the eigenvalues, so every order is a weighted sum over the spectrum.

Values are unchanged: identical on 3000 molecules sampled from MoleculeNet,
TDC and MoleculeACE, over all 19 walk count columns.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-12-bcut` - review and merge in order.

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
13. #677 - walk counts  **<- this PR**
14. #678 - conformer descriptors
15. #679 - atom, bond and constitutional counts
16. #680 - topological charge and Zagreb
17. #681 - ABC and molecular distance edge
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5e464a51df38`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.