# Issue

**Title:** Adds ORCA version extraction

## Description

This PR adds a `_get_version_no_output` method to the ORCA wrapper, which in turn enables checking if the vdw charge scheme needs to be turned off when running analytical Hessian calculations. Unfortunately, this cannot be tested in CI 😕

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `44d9b4b334b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.