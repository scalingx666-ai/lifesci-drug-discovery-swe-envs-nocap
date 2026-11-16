# Issue

**Title:** Fix tests of scaffold functionality

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
Fixes the tests of the new scaffold feature from PR #910 

The `from_json` function adds entries as a background job, so we have to enable the job runner as well as wait for them to finish.

(also renames the test :) )
## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c3236346d628`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.