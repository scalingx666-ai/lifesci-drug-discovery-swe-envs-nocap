# Issue

**Title:** Fix headers with system InChi

## Description

I guess the bundled header would still have been used before 3e6cb82 if include/inchi hadn’t been cleaned up by package maintainer.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `19c575ba3946`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.