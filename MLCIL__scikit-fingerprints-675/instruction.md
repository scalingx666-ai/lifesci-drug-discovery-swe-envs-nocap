# Issue

**Title:** Mordred: read the VSA descriptors from RDKit in bulk

## Description

Reads the MOE-type VSA descriptors with one RDKit call per group instead of one call per bin (52 calls -> 5), and groups the atoms by E-state type in one pass instead of rescanning them for each of the 79 types.

Everything is still computed by RDKit; output is identical on 300 molecules sampled from molpile (1613 features each), and the full Mordred calculation is about 3.5% faster.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-10-barysz` - review and merge in order.

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
11. #675 - VSA descriptors read from RDKit in bulk  **<- this PR**
12. #676 - BCUT (not computed before)
13. #677 - walk counts
14. #678 - conformer descriptors
15. #679 - atom, bond and constitutional counts
16. #680 - topological charge and Zagreb
17. #681 - ABC and molecular distance edge
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8af4ac8d69e2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.