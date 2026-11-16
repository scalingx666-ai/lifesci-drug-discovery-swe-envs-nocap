# Issue

**Title:** Avoid redundant CI runs in PRs on push

## Description

Currently, CI runs are triggered by `push` and `pull_request`, which leads to two runs for every check in a PR. This can be fixed by restricting runs on `push` only for a push to the main branch, i.e., when merging the PR.

I also added path ignores to avoid code builds for changes in the documentation. However, this feature seems to be buggy atm ().

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `bbb79576ff08`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.