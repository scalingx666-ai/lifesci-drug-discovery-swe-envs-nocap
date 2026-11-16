# Issue

**Title:** Allow GitHub Actions to run on both "master" and "main"

## Description

New GitHub Repositories have their first branch called "main" now
instead of "master." Details [here](https://github.com/github/renaming).

Because some people might start with a blank repository from GitHub,
and some people may start from `git init`, i've added support for
both in GitHub Actions to handle both start points.

There is a corner case if someone creates the repo on GitHub, uses the
cookiecutter (which `git init`), then the default branch names might
clash. But until we start to see this conflict be an issue, I don't
think there is extra engineering which needs to be done at this moment.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9c0fe5c7bf62`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.