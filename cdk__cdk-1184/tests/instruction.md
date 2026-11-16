# Issue

**Title:** FIx #1183 InChITautomerGenerator on AtomContainer2

## Description

The InChI tautomer generator deleted atom/bonds but not stereochemistry leaving the 'skeleton' in an invalid state. The simple fix was to clear the stereochemistry from the skeleton (it was retained on the input molecule). Rather than delete the atoms one by one inefficiently it is better to just create the skeleton as we need it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83396e451a62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.