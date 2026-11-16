# Issue

**Title:** Mordred: compute the BCUT descriptors

## Description

The BCUT module was written but never called: the calculator did not list it,
so all 24 BCUT columns came out NaN for every molecule. This wires it in and
rewrites it to work off the shared properties.

- the six weighted Burden matrices are built and decomposed as one stack,
  instead of one matrix and one eigendecomposition per property
- the diagonal weights come from AtomicProperties, so the Gasteiger charges
  and intrinsic states are the ones already computed for other descriptors

This changes the output: the 24 BCUT columns go from NaN to real values,
except for disconnected molecules, which stay NaN by definition (10 of the 300
molecules sampled from MoleculeNet, TDC and MoleculeACE). No other column
changes.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-11-estate-vsa` - review and merge in order.

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
12. #676 - BCUT (not computed before)  **<- this PR**
13. #677 - walk counts
14. #678 - conformer descriptors
15. #679 - atom, bond and constitutional counts
16. #680 - topological charge and Zagreb
17. #681 - ABC and molecular distance edge
</details>

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `98ff4c9fd9c3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.