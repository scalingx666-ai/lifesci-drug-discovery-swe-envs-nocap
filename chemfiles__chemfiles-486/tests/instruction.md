# Issue

**Title:** Handle whitespaces in more places in LAMMPS Data format

## Description

Fix #485 

Corresponding test file: https://github.com/chemfiles/tests-data/blob/1256f2dbf7370528fb8361b28d78e4534633b1f7/lammps-data/whitespaces.lmp

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66e387c0ebea`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.