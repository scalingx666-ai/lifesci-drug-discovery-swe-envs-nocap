# Issue

**Title:** Fix copying of TMolecule

## Description

By some reason, GCC 12.2 does not copy some data between TMolecule objects and, therefore, there is some trash in output like (it is xtbopt.xyz):
<img width="472" alt="image" src="https://github.com/user-attachments/assets/274e16f4-7ee5-4e9d-8539-d4892f7ac7a7" />

This patch fixes it. Not sure that I found all places, but at least GFN2 geometry optimizations work well.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2010acef4def`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.