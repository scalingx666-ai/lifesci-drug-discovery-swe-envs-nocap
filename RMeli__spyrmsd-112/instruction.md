# Issue

**Title:** Documentation and CLI for backend selection

## Description

## Description

Close #108 and close #109.

This PR adds documentation related to #107:
* Add doc to `README`
* Add doc to tutorial (website)
* Add docstrings to functions (unfortunately they don't appear in the API documentation since they are private)

This PR adds the `-g/--graph-backend` to manually select a backend from CLI.

Additionally, the following cleanup is done:
* Use `importlib.utils` to check if a package is available, without importing it
* Re-work how internal alias dictionaries are constructed
* Make backend test more general, in preparation to #111

## Checklist

- [x] Tests
- [x] Documentation
- [x] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0b917f860a0c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.