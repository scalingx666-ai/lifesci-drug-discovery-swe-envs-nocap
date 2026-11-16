# Issue

**Title:** Graph Isomorphism with Atom Matching

## Description

## Description

Graph isomorphism now works with atom matching. Two nodes are considered equivalent if they have the same atomic number (`atomicnum` attribute).

This PR leads to results in great agreement with Open Babel `obrms`. Differences in RMSD are smaller than `5e-5 Å`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `51b1d40509e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.