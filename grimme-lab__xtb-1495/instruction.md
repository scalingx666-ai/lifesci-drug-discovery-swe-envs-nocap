# Issue

**Title:** Remove periodic information from molecular systems for normal xyz printout

## Description

Right now, by default, lattice and periodicity information is passed into the structure object, leading mctc-lib to print an extended xyz file with the lattice vector information even for molecular systems. I omit those to restore the normal xyz output. Since this occurs only very rarely (mostly the TMolecule type is used), I can confirm that this has no additional effects on the calculation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `93ff3492bf9a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.