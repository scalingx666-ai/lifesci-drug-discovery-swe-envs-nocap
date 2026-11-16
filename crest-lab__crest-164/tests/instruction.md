# Issue

**Title:** Fix GitHub workflows build (use ifort 2022.2.1 instead of latest)

## Description

This fixes the latest GitHub workflows build and adds a continuous release job to it.
The continuous release will be found at https://github.com/crest-lab/crest/releases/tag/latest

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f547327870b2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.