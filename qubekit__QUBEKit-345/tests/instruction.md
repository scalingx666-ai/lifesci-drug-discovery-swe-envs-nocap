# Issue

**Title:** Use the amoeba plugin handler for Urey-Bradley terms

## Description

## Description
This PR updates the old handling of Urey-Bradley terms from QForce to use a dedicated handler in QUBEKit. These are now exported to OpenMM via the AMOEBA plugin handler which means they can be loaded with no virtual bonds and will have the correct non-bonded exceptions.

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ac67d937d18c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.