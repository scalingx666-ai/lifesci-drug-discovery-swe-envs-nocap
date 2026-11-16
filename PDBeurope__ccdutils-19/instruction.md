# Issue

**Title:** Improving depiction diagrams for dative bonds to metal (like HEM)

## Description

This is a suggestion to use "ZERO order bonds" when there is a dative bond to a metal atom that results in a dotted line. For example HEM produces a diagram:


![HEM](https://github.com/PDBeurope/ccdutils/assets/8986794/de5e5929-ec56-48db-8384-94393e4c7c0c)

see comment below for the current diagram that uses atom charge adjustment rather than altering the bond order.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5754952ef5e4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.