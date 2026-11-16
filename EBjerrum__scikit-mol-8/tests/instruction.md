# Issue

**Title:** ci: add workflow to deploy to pypi

## Description

This PR adds a workflow to deploy scikit_mol to pypi for commits that are tagged.

The way you use this is the following:

- develop your module on github and everytime you want to make a new release you create a tag
  ```console
  # the current latest commit on main that should be released as a new version
  $ git tag v0.1.2
  $ git push origin v0.1.2
  ```
- this will trigger the ci and build a new version of the package and deploy to pypi
- I recommend having the tags adhere to semantic versioning `vX.Y.Z`


To set up the required tokens, goto pypi and sign up.
Goto your account settings and scroll to the API token section. Create a new API token with scope for everything (note: after your project was created you can replace the token with a token that has scope only for your project)
Copy the token and add it as a secret in your github repository (Settings > Secrets > Actions, --> Create New Repository Secret) The secret name should be `PYPI_PASSWORD`.

When the deploy pipeline after a tagged commit succeeds, your new version is available on pypi.

People can then just `pip install scikit-mol`

If anything is unclear, let me know!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `778fde7a352a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.