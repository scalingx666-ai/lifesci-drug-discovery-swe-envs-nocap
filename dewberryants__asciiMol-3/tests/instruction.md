# Issue

**Title:** Added pypi on release workflow

## Description

This PR adds a Github Action that will post your package to pypi whenever you do a Github Release (or you manually trigger in the actions panel). You'll need to add make a pypi account and [add your token to your repo secrets](https://docs.github.com/en/actions/security-guides/encrypted-secrets#creating-encrypted-secrets-for-a-repository) as `PYPI_API_TOKEN`

I also modified README with `pip install` instructions and a badge. Great project!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1fc9a80ed49c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.