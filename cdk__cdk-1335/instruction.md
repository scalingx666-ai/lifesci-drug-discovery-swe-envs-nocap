# Issue

**Title:** Fix the congestion update in layout refinement

## Description

`Congestion.update(int[], int)` inverted each pair's contribution twice, storing dist^2 instead of 1/dist^2, so the refiner's running score drifts and overlaps go unnoticed. `COC(=O)C=C(C(=O)O)C(CC1=C(Br)C(O)=C(O)C(Br)=C1Br)C(=O)O` was laid out with substituents on top of ring atoms.

The update now stores 1/dist^2 like the rest of the class, so the running score matches one computed from scratch.

The test commit fails without the fix.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ddafddc16a8e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.