# Issue

**Title:** NWChem: Run dipole moment calculation

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This pull request allows qcng to run properties calculations.  It also includes changes to harvester.py that reads the dipole moments from nwchem output files.  The PR also includes a test_dipole() function.
## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Allows qcng to run properties calculations and parse dipole moments output.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `84a524cabd53`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.