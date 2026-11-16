# Issue

**Title:** Fix McConnaughey bug

## Description

## Changes

Fixes a typo in McConnaughey bulk similarity that resulted in nondeterministic and buggy behavior.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6faa0dc80abb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.