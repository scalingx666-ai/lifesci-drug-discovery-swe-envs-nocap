# Issue

**Title:** Mordred: vectorize the conformer descriptors

## Description

The 3D descriptors each walked the conformer molecule themselves. MoRSE built
its 32 distance terms one atom pair at a time for every one of the seven
weighting properties; the gravitational indices summed over bonded and
unbonded pairs in Python; the CPSA surface areas were accumulated per atom.

- morse takes the conformer atomic numbers as an array and evaluates all
  distances and weights as one broadcast
- the solvent-accessible surface areas come back as an array, and the CPSA
  partial areas are masked sums over it
- gravitational_index and geometric_index read their distances off the shared
  3D distance matrices

The Gasteiger charges for CPSA now come from the conformer molecule itself
rather than from the hydrogen-explicit molecule the 2D descriptors use: those
two have different atom numberings, and CPSA pairs the charges atom by atom
with surface areas computed from the conformer.

Verified by the 3D reference tests (MoRSE, CPSA, SASA, geometric and
gravitational indices) and by the fingerprint-level comparison against
mordred-community, all of which pass. Conformer embedding is not reproducible
run to run, so there is no whole-output diff for the 3D block the way there is
for the 2D one.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-13-walk-count` - review and merge in order.

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
14. #678 - conformer descriptors  **<- this PR**
15. #679 - atom, bond and constitutional counts
16. #680 - topological charge and Zagreb
17. #681 - ABC and molecular distance edge
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc5e9efb901a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.