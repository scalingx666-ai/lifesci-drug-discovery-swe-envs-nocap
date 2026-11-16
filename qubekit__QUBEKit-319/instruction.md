# Issue

**Title:** Offxml plugin

## Description

## Description
This PR updates the offxml combine method to use a plugin which avoids the use of parameter eval statements. Here we assign each atom a volume via smirks and use a custom vdW handler with Rfree, alpha and beta global attributes which can be optimised with Forcebalance. We also add support for TIP3P water in the offxml. If parameters are not to be optimised a standard offxml is made using the default vdW handler.


## Status
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2ba56dc0e4f7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.