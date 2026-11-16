# Issue

**Title:** Fixed a bug in Standardize script

## Description

Hi,

The Standardize script had a bug. If you set "neutralize=False" it returns an error. I just fixed it.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d175c61af2a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.