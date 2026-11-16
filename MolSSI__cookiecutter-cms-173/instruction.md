# Issue

**Title:** Improves cookiecutter post generation scripts

## Description

This PR makes a few improvements to the post-generation cookiecutter scripts, particularly the `git_init_and_tag` function.

* `invoke_shell` is fixed so that output (including error from `git status`), resulting in the somewhat confusing `git` error message to no longer print.
* `expected_error` argument to `invoke_shell` is changed to `error_ok` - this seems more clear.
* return code is added to `invoke_shell`
* return code (instead of output message) is checked for `git init`.
* `--init-branch=main` is replaced with `git branch -M  main` after first commit. This will enable cookiecutter to work with older git versions. `--init-branch=main` is only an option for git > 2.28, but `git branch -M main` after the first commit will work for versions before 2.28.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `401afa96a3e0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.