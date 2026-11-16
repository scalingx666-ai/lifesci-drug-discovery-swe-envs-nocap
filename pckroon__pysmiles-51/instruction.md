# Issue

**Title:** Ez multi

## Description

This PR fixes E/Z assignment for some edge cases (e.g. `F\C=C\C=C\F`). In addition, it raises an error for invalid SMILES like `(F\)C=C`. In doing so it unfixes extended CIS/TRANS (e.g. `F\C=C=C=C\F`). I think it is worth not including these at the moment. It does throw an error for the extended CIS/TRANS. It also handles multiple CIS/TRANS per double bond (e.g. `C(\F)(/F)=C(/Cl)(\Br)` and checks if they are compatible.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1071fbf78929`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.