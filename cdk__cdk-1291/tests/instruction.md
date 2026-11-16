# Issue

**Title:** Fix a minor corner case in hydrogen normalisation.

## Description

We add hydrogens to tetrahedral atoms only if the adjacent stereo elements stop

For example this does not need extra hydrogens:

<img width="173" height="114" alt="image" src="https://github.com/user-attachments/assets/e92402a5-206f-4048-a118-350cbab3399e" />

This example does: 

<img width="195" height="89" alt="image" src="https://github.com/user-attachments/assets/a9c1ea8d-7dc8-4f08-9721-44c89dc2f9ce" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4639c7677549`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.