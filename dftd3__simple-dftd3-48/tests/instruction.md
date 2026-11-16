# Issue

**Title:** Implementation of Actinides.

## Description

## Description
Added actinides support to the Fortran version, following the Torch autodiff DFT-D3 implementation by [FreeSoulIG](https://github.com/FreeSoulIG).

## Changes Made
- Added support for actinides in the Fortran version, based on the changes made in commit 
- Implemented necessary new vdw and c6ab parameters
- Added new tests for the actinides

Crosschecked and validated results from both implementations to ensure accuracy. The test suite successfully completed without any errors.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cdd0a85600bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.