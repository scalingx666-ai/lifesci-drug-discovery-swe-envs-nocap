# Issue

**Title:** Remove reset running functions

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

There was a function to reset running records in the socket which could never be called through the API. It used to be available as records could get stuck on zombie workers. However, those loopholes have been closed for years and should not happen anymore.

This was confusing because things like dataset reset_records seemed like it would reset running, but that was not possible. This makes that explicit, hopefully.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `91e58bb6a646`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.