# Issue

**Title:** Return non sanitised mol if the sanitisation fails

## Description

Updated to return the non-sanitised version of mol object if the implemented sanitisation process fails even after an iteration of 10 times. Earlier, when the sanitisation process fails, the mol object returned was after the changes made during the sanitisation process. This caused unusual valancies on some atoms. 

The rdkit version is fixed to 2023.3.3, the latest version 2023.09.1 is failing while generating InChI for ligands with DATIVE bond type. An  is raised in rdkit github repo for the same.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3c15c4e90190`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.