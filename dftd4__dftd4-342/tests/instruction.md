# Issue

**Title:** add dependabot

## Description

For instance
https://github.com/dftd4/dftd4/blob/32933e61e68dd5ccc027129bbeae5ec59a83e2cb/.github/workflows/fortran-build.yml#L127
is outdated—the latest is v6.

dependabot automatically updates the actions.

Note that you have to enable "Dependabot version updates" in <https://github.com/dftd4/dftd4/settings/security_analysis>.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `32933e61e68d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.