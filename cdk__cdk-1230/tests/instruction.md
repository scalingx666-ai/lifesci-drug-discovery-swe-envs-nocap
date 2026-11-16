# Issue

**Title:** Move around some XML config files.

## Description

- mm2/mmff94 only used in legacy so moved there.
- mol2 is now in cdk-io where it is used Mol2Reader
- pdb is now in cdk-extra although this file is only used on cdk-extra (protein pocket finder)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e93b8c3f1b9c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.