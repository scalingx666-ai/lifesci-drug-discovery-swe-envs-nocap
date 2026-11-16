# Issue

**Title:** Fix `farthest_point_sampling` and `initialization` interplay

## Description

Uses `argsort` to being able to correctly add predefined indices that correspond to position in the unsorted (original) instead of the sorted list

Examples:
<img width="723" height="416" alt="image" src="https://github.com/user-attachments/assets/d94d6731-2fdf-4d86-a9ca-b6226a3f8aa8" />

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `472f1bcf0777`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.