# Issue

**Title:** Localized orbitals via tblite

## Description

Adds support for Foster-Boys localization and Molden output of the orbitals with tblite. This PR first introduces only the LMOs themselves. I will add support for docking with tblite in a separate PR. 

This also addresses #483 by supporting Molden LMOs for visualization. 

requires first

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6294cf418f7b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.