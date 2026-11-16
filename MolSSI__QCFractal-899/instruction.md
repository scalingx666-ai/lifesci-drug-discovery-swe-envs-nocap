# Issue

**Title:** Fix duplicate env in fulltest GHA

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

The "fulltest" GHA set up a nice conda env with qcportal, then also used a venv. This attempts to clean that up.

## Status
- [X] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc5df5361c1f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.