# Issue

**Title:** Rename folder containing GitHub Actions yamls to `.github` so discoverable

## Description

@ale94mleon Really nice work on this package!

As I was reading through, I noticed the GitHub Actions workflow files were in a `github` directory, but GitHub Actions expects a `.github` directory and, if it exists, looks there for workflow files ([source](https://docs.github.com/en/actions/get-started/understand-github-actions#workflows)):

> Workflows are defined in the .github/workflows directory in a repository.

You'll see the GitHub Actions CI is automatically triggered from opening this PR with this change (as specified in the `tests.yml` and `codeql-analysis.yml` files):

https://github.com/ale94mleon/BindFlow/blob/b08addbe68a2d3066fa7aed2eebc71c7780a7414/github/workflows/tests.yml#L9-L10

https://github.com/ale94mleon/BindFlow/blob/b08addbe68a2d3066fa7aed2eebc71c7780a7414/github/workflows/codeql-analysis.yml#L17-L19

However, since I don't have write access to this repo, I believe you'll have to [approve this workflow run](https://docs.github.com/en/actions/how-tos/manage-workflow-runs/approve-runs-from-forks) for the actual CI checks to run.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b08addbe68a2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.