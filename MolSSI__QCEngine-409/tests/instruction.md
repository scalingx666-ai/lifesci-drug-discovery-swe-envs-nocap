# Issue

**Title:** Psi4 random fail restarts

## Description

## Description
<!-- Provide a brief description of the PR's purpose here. -->
This PR  by adding a valid error message which raises a `RandomError` needed to restart the calculations.

## Changelog description
<!-- Provide a brief single sentence for the changelog. -->
Psi4 tasks are now correctly restarted when there is no valid error message.

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [ ] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1822ea441744`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.