# Issue

**Title:** Fix build workflow

## Description

- add permission for `GITHUB_TOKEN` (as described [here](https://github.com/JamesIves/github-pages-deploy-action#getting-started-airplane))
- update versions of actions

Workflow fails due to missing write permissions in: Settings -> Actions -> General -> Workflow permissions.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cdd0a85600bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.