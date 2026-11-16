# Issue

**Title:** Refactor postselection and subsampling logic

## Description

- Introduce the `postselect_by_hamming_right_and_left` function which does exactly what its name says.
- Use the new function in `diagonalize_fermionic_hamiltonian`, making the logic more clear.
- Deprecate `post_select_by_hamming_weight` which has a non-intuitive return value.
- Deprecate `postselect_and_subsample` because it's no longer needed.

 

TODO add release note

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a0a59c9b6bde`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.