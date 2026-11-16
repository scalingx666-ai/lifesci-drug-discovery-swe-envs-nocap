# Issue

**Title:** Fix gfnff topology restoration

## Description

,  

#987 was introduced by  where (among other changes) `TGFFTopology` `blist` and `nbond` attributes were no longer set, with most usages replaced by the corresponding attributes of `TNeigh`. The 2D->3D conversion code missed this remapping, so the harmonic restraints were using faulty `topo%nbond` and `topo%blist` rather than the up to date `neigh%nbond` and `neigh%blist` as intended. Updating those resolves the issue.

#1132 stems from artificial bonds between the ligand and receptor being formed during close contacts. Some of these "bonds" would be nonsensical like an H-H bond. The proposed fix is to restore the separated bonding for ligand and receptor, just allowing them to interact non-covalently.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b31754bf3c7c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.