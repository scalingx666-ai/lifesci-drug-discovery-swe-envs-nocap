# Issue

**Title:** Bump setup-fpm to v7

## Description

Older versions always pull the latest fpm version, which now breaks after compiler name was added to the release artifacts (see ).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `83f78b546ac5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.