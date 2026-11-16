# Issue

**Title:** Add support for loading selection/highlight from CXSMILES and MDL Mol…

## Description

…files.

- We have an existing interface IChemObjectSelection which support highlighting when rendering. These needed to be moved to the cdk-interfaces module.
- In CXSMILES we can use the EPAM extension of ha: and hb: to load highlighted bonds/atoms
- MDLV3000 has HILITE collection which we can use
- Fix a bug with the writing of MDLV3000 stereo groups, the first digit needs to be the number of things in the set

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ae0d100382d6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.