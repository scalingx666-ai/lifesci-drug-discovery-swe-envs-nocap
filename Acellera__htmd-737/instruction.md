# Issue

**Title:** Fixes bug with MDTrajread

## Description

After the PR which doesn't store zero coordinates when loading pure topology files (ala prmtop), the MDtraj reader was crashing. The reason is that the MDTrajRead writes out a PDB file to load the trajectories and the PDB writer was crashing when not finding any frames or coordinates in the molecule.
I now made the PDB writer write out zero coordinates when there are no coordinates in the molecule which fixes the bug. Also added a test for it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `16bf3485ba67`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.