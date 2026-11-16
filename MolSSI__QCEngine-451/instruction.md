# Issue

**Title:** Use sys.executable over explicit call to python

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
The psi4 frontend calls `python` which may not be available or not have psi4.
This PR replaces the call with `sys.executable`.



## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b56a2aa9bdfc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.