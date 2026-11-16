# Issue

**Title:** Update ngl ts branch so we can click to display distance, angle, dihedral angle

## Description

From @arose 

`
I recently added mouse bindings to do distance, angle, dihedral measurements. In the ts2 branch hold down alt (not shift as stated earlier) and click 2 to 4 atoms and then click on the last atom again to get a measurement. Click on all the atoms of a measurement and click the last one twice to remove it.
`

<img width="1160" alt="screen shot 2017-11-21 at 10 34 48 pm" src="https://user-images.githubusercontent.com/4451957/33108867-74767378-cf0c-11e7-8760-c28be8327166.png">

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f9faf39f66d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.