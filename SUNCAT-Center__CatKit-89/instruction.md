# Issue

**Title:** Connectivity cutoff fix

## Description

The cutoff for the connectivity matrix wasn't working. 

Made a fix by getting the distance for each individual connection, and applying the cutoff there. 
The pair-distances (and their indices) are returned if requested.

Update: also make it possible fine-tune the covalent radii cutoff in the simple cutoff_neighbors connectivity, since these can sometimes be too small and bonds not counted.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c721098264be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.