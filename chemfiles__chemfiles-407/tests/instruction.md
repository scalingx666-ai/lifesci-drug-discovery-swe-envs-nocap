# Issue

**Title:** CIF/mmCIF improvements

## Description

This PR should fix all chemfiles' side issues reported in  I'll work on the MDAnalysis side for the remaining issues.

- make the mmCIF reader more strict, and move COD/CCSD files support to CIF reader
- make `guess_format` distinguish between CIF and mmCIF files if the extension is .cif


@frodofine since you wrote the mmCIF code, could you give this a look?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3e82aebde9c4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.