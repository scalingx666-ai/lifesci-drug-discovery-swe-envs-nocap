# Issue

**Title:** orient: make build deterministic

## Description

The orient build is still not deterministic, as long as we keep the `leaveDotGit = true`. I've switched to deterministic fetching and included a patch to the python code, that tries to read the git output to get the commit, and replaces it by a simple query of an environment variable.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4636c47059af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.