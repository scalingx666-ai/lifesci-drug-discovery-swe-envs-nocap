# Issue

**Title:** NWChem: Add ability to turn off autoz

## Description

## Description

NWChem's autoz function generates a Z matrix and [is known to have issues with large molecules](https://nwchemgit.github.io/FAQ.html#autoz-fails-to-generate-valid-internal-coordinates-now-what). 
This PR adds an option to allow QCEngine to run NWChem with autoz turned off. 

## Changelog description

Added option for disabling autoz in NWChem

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7bd25219f5f4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.