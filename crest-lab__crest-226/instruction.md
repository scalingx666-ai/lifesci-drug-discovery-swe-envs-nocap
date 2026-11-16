# Issue

**Title:** Allow QCG site directed solvation

## Description

With the site directed docking feature of the aISS algorithm it is now possible to solvate specific atoms of the solute. Therefore, the "-directed <FILE>" keyword is implemented. With this, a file is read in containing the atoms that should solvated and the number of solvents to add at this positions in one line. Multiple regions can be defined in multiple lines.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `731611c64b6f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.