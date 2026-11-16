# Issue

**Title:** fix nwchem

## Description

<!-- Thank you for your contribution! -->

## Description
Sorry, I approved faulty code. Actually, all NWChem is broken with "NameError: name 'cc' is not defined". This fixes.

## Changelog description
- Fix typo breaking NWChem

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [ ] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `30030d593e2b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.