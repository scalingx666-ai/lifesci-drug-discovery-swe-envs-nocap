# Issue

**Title:** git init

## Description

This PR modifies the post_gen_project script so that `git init` and `git tag` are only performed if Cookiecutter is not in a repository and there is no existing tag.

Addresses issue #85

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `67cfcd198285`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.