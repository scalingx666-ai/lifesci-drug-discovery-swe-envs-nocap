# Issue

**Title:** Mordred: compute the autocorrelations from distance masks

## Description

The autocorrelation descriptors looped over lags 0-8 in Python, and for each
lag over every atom pair, reading the atomic property of each atom through a
per-atom function. Every one of the eight weighting properties repeated that
whole traversal.

The properties now come from AtomicProperties as arrays, the distance matrix
is turned into one boolean mask per lag once, and each family (ATS, ATSC,
AATS, AATSC, MATS, GATS, Moreau, Geary) is a matrix product or a masked sum
over those.

Values are unchanged except for the centered families at the lags where the
result is zero by construction: 32 columns differ by at most 1e-13 absolute,
with both values below 1e-12 - floating point noise around zero, on 300
molecules sampled from MoleculeNet, TDC and MoleculeACE.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-08-eta` - review and merge in order.

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
9. #673 - autocorrelations  **<- this PR**
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f32600573be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.