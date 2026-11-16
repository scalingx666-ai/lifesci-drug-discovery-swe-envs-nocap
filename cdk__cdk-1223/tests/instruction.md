# Issue

**Title:** Rgroup Improvements

## Description

Some required improvments to RGroup handling (for JChemPaint).

These changes setup explicit attachment atoms (wiggly line on a bond) for RGrgoup substituents. In MDL they are not stored this way so we need to add/remove them when we read/write and generate the confermations.

Likewise bond attach order specifies the bond labelling/order when a R group has multiple leaving bonds.

Example of what it looks like in JChemPaint.

<img width="700" height="580" alt="Screenshot 2025-09-10 at 11 30 32" src="https://github.com/user-attachments/assets/1adce2e5-8532-4aef-b77e-d0b104d43496" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6502177cab85`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.