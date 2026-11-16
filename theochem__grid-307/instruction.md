# Issue

**Title:** Add inverse derivative methods to BaseTransform

## Description

Adds inverse-derivative methods to `BaseTransform`:
 `deriv_inverse`
 `deriv2_inverse`
`deriv3_inverse`

Added FD test for each one.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `706ea643713c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.