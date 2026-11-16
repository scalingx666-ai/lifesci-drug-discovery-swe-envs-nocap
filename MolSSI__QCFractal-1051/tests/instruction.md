# Issue

**Title:** Add ability to set Parsl scale-in strategy

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
Implement the ability to set the strategy parsl uses for scaling in blocks. This can be helpful when there are fewer tasks than blocks or nodes, and you don't want to have slurm jobs running unnecessarily.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `257d092eee3e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.