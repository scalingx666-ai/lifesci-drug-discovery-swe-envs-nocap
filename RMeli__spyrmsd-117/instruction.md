# Issue

**Title:** Use IDs in tests

## Description

## Description

Some test names are not very descriptive, and can create confusion (see  ). This PR introduces IDs in tests in order to have better and more explicit test names (when running with `--verbose`, as in CI).

Close #115.

## Checklist

- [x] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `aa1cd7a63592`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.