# Issue

**Title:** Move branch and formatVersion to runtime properties

## Description

Branch and format version were actually defined in several different places, and it might be easy to forget to modify it in both places. We've actually forgot to do so, and that led to #66 

This PR places build branch and format version to runtime properties `.ini`, so now we should only change formatVersion in one place, and shouldn't change branch at all. If smb wants to build jupyter locally and use libraries branch different from what s/he's on, s/he should set `build.branch` gradle property locally.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f4737886e0f1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.