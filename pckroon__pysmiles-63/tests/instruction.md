# Issue

**Title:** Speed up `add_explicit_hydrogens` on large molecules

## Description

The for loop  in `add_explicit_hydrogens()` called `max(mol)` twice for every heavy atom to find the next free node index. Each call walks the whole graph, so the runtime grew with the square of the molecule size. 

Since new hydrogens are always numbered above the current maximum, we only need to find the max once and then count up. The hydrogens still get the same indices as before.

Testing this on a 56k-atom polymer takes about 0.1 seconds vs 28 seconds without this change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f96039fc19d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.