# Issue

**Title:** Mordred: build the detour matrix from the distance matrix and its rings

## Description

The detour matrix was built by splitting the molecular graph into biconnected
blocks with networkx, solving the longest simple paths inside each block by
brute-force DFS, and stitching the blocks back together through their
articulation nodes. The stitching, the graph conversion and the networkx
dependency all go away here.

Outside the rings there is only one simple path between two atoms, so the
detour distance is the ordinary distance; a path can differ from the shortest
one only where it crosses a ring system. Each ring system is added on top of
the distance matrix as a correction - how much longer the longest way through
it is than the shortest one - read off at the atoms where a path enters and
leaves the system. A simple path cannot leave a ring system and come back, so
the corrections are independent of one another. Plain rings need no search at
all: the two ways round between two atoms make up the whole ring.

The ring systems come from merging the perceived rings that share at least two
atoms, which is not always the whole story: RDKit's rings do not cover every
cycle of a cage-like molecule, and two rings sharing a single atom can still
belong to one cage, where a path leaves through one shared atom and returns
through another. Both leave a cycle spanning more than one ring system, which
_are_ring_systems_complete() detects by comparing the cycle rank of the
molecule against the ranks of its ring systems, in one pass over the bonds.
When they do not match, the systems are taken from the components left after
removing the bridges, which is exact and costs an extra DFS.

Verified against the previous implementation on every molecule of MoleculeNet,
TDC and MoleculeACE - 591,388 connected molecules, of which 19,735 disconnected
ones return NaN under both. The matrices are identical everywhere. Without the
completeness check one molecule differs (an HIV di-iron cage, DetourIndex 5441
against the correct 9633), and the check flags exactly that one. Fuzzing over
23k random polycyclic skeletons against brute-force longest simple paths finds
48 more such cages, all of them flagged, with no false alarms.

The 14 detour features differ by up to 2e-7 relative, from the corrections
being accumulated in the float64 distance matrix. The check itself costs about
7% of the descriptor, and its fallback fired on 1 molecule in 591,388.

---

Splits up #661 into reviewable pieces. Based on `mordred-opt-06-subgraphs` - review and merge in order.

<details>
<summary>The stack</summary>

1. #665 - feature names resolved per module
2. #666 - AtomicProperties
3. #667 - hydrogen-explicit matrices derived
4. #668 - spectral attributes over a stack
5. #669 - RingSets
6. #670 - subgraph enumeration (chi, path counts)
7. #671 - detour matrix  **<- this PR**
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

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c808b0b73eea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.