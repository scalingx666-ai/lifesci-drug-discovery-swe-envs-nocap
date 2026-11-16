# Issue

**Title:** Reduce batch size in view creation

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

When creating dataset view files, a batch size of 200 was used. This number was a wild guess. However, in datasets that contain large records (particularly wavefunctions) this is too large and can cause excess memory usage. This can safely reduced without much performance impact, but should reduce memory usage.

Should help with #946 

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a80c7cd6dacb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.