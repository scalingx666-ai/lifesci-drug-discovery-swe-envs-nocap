# Issue

**Title:** Fix some warnings

## Description

I have reordered cycles in constrain_pot.f90 and optimize them a little bit.

In frag_hess.f90 the interfaces were written improperly. With this patch, it is fixed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `88182d28a757`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.