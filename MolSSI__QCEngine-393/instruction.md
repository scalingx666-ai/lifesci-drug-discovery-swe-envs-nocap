# Issue

**Title:** update gCP levels and extend D4 defaults

## Description

<!-- Thank you for your contribution! -->

## Description
For psi4 to run B97-3c and r2SCAN-3c the gCP harness needs an update to the allowed methods (limited to the new 'mctc-gcp'). () r2SCAN-3c requires manipulation of additional parameters. `dftd4` has been updated to allow this. The D4 harness update sets the additional defaults. Because the dftd4 toml file does not contain these parameters the D4 harness sets them.

 

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Adds `b973c` and `r2scan3c` methods to the gcp and dftd4 harness.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5935117a42fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.