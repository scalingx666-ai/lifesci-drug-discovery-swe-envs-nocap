# Issue

**Title:** Add type hints

## Description

Requested Reviewers: @andrewtarzia
*Note for Reviewers: If you accept the review request add a :+1: to this post*

Refactored the key makers to explicitly provide type hints rather
than rely on the default implementation. It is sometimes useful to
be able to rely on the more specific type of the key.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `34a2d1460b54`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.