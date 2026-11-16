# Issue

**Title:** Generate & use once-canonical SMILES

## Description

(for now)

I also commited the `.smiles` file, that way we can easily keep track of changes.

At the bottom of the Grover notebook I added a check to make sure the index of the dataframe is exactly equal to the entries of `lincs_trapnell.smiles`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `768478443023`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.