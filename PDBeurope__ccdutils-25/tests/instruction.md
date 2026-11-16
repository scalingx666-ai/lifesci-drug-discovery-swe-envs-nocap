# Issue

**Title:** PDBE-6878: Sort nodes of graph based on residue id and chain

## Description

The graph representation of boundmoelcule contain residues as nodes. The id of boundmolecule is decided based on the id of nodes. But before assigning id to boundmolecule the nodes of the graph need to be sorted in order make sure that consistent id is given.

For example:

graph_1: J1-J2
grpah_2: J2-J1

sorting nodes will make sure the id of bm1 and bm2 to be J1-J2.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5754952ef5e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.