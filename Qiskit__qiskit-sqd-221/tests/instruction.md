# Issue

**Title:** fix bitstring_matrix_to_ci_strs docstring

## Description

Removes the "flips the bits" bit because the bits are not flipped. The comment may have applied to a previous version of the code.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e4883f92cae7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.