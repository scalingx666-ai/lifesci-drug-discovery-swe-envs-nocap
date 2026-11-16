# Issue

**Title:** Enable continuous delivery of statically linked dftd4 versions

## Description

Create a bleeding edge release for new DFT-D4 version to allow easier testing. This feature is enabled on push, meaning developers enabling actions on their fork are able to use this workflow to create local versions of their branches.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7da9c58b3980`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.