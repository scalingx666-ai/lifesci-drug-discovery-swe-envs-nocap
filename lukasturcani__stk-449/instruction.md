# Issue

**Title:** Add deprecation notice for `pdb` reading

## Description

Related Issues: #446 
Requested Reviewers: @andrewtarzia 
*Note for Reviewers: If you accept the review request add a :+1: to this post*

Removes the note that users can load `pdb` files from the docstring of 
`init_from_file`, in order to stop new users from using these files for loading
molecules. Loading will still work for now, but users will receive a `FutureWarning`
telling them that they should switch to `.mol` files.

The reason this deprecation is necessary is that `pdb` files do not encode bond
orders and the loaded building blocks may therefore have wrong or unexpected
connectivity. By explicitly not supporting this file type we make sure our users
carefully consider the bonding of their molecules and avoid surprises.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0f4d634a034d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.