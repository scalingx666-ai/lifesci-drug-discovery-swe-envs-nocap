# Issue

**Title:** fix: correctly handle chirality information

## Description

This PR fixes a bug in the handling of chirality information. Previously, all chirality tags were incorrectly assigned as "unknown chirality" regardless of the input, leading to incorrect results when processing small molecule data.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f515995cfca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.