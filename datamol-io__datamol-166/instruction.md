# Issue

**Title:** gh: refactor community files

## Description

This PR aims to moves the `CONTRIBUTING.md`, `CODE_OF_CONDUCT.md`, `CODEOWNERS` and `SECURITY.md` file inside the `.github/` dir. Github looks for a contribution guideline file in the following order: `.github dir > project root > docs dir` ([source](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/setting-guidelines-for-repository-contributors)). Moving the file to the `.github/` dir leads to a minimal project structure without any functional change.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `eb690755c7fa`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.