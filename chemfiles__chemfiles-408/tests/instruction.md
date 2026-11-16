# Issue

**Title:** Use github Actions for CI in the 0.10 branch

## Description

I initially wanted to keep Travis there, but fixing CI for #406 burnt through all the credits for July, so this is not sustainable.

All commits where cherry-picked from #394

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `33160ea40ca1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.