# Issue

**Title:** Update to support MDI v1.0.0

## Description

<!-- Thank you for your contribution! -->

## Description
The MDI interface implementation in QCEngine currently only supports the pre-release version of the MDI Library.  This PR updates the interface implementation to accommodate changes that were introduced in the 1.0 version of the MDI Library.  The primary modifications include changes to (1) the way NumPy arrays are handled by the MDI Library and (2) updates to the manner in which node information is communicated.

## Changelog description
Add support for MDI Library v1.0.0 release

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `141fcc787206`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.