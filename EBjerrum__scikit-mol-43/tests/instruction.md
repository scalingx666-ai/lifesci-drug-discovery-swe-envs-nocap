# Issue

**Title:** adapting to new rdkit fingerprint generators.

## Description

This is adressing the deprication warnings mentioned in  #41 and therefore implements a set of new transformers.

Design concept is a bit verbose, but I wanted to be as close as possible in the old feeling and as efficient as possible ;)
Such it is possible to replace the old rdkit based implementations seemingly;)

We could consider doing this
already ;)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `523b1905bcf1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.