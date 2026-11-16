# Issue

**Title:** Add details on NotImplementedError exceptions

## Description

## Description

Some code paths lead to `NotImplementedError` exceptions. The exception are sometimes unclear an surprising to users (). Close #89.

This PR adds proper error messages, to clarify the problem.  

## Checklist

- [x] Tests
- [x] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b5532dd1b677`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.