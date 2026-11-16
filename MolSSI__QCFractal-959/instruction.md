# Issue

**Title:** Change to using spawn rather than fork

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

There are some warnings popping up that mixing threads and `fork` is not that good of an idea. After #955 and #957 things should be ready for changing to using `spawn`. Creating new processes this way is slower, but safer.

Everything passes locally, but let's see how GHA handles this

## Status
- [X] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0efd61073848`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.