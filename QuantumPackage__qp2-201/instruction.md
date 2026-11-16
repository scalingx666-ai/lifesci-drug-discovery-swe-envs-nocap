# Issue

**Title:** update i_H_j

## Description

Remove bitstring_to_list
Add some provide at the beginning to avoid problems with irpf90 when the mono e integrals are changed

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `be6c230f5264`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.