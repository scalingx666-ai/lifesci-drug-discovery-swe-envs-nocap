# Issue

**Title:** Update server stats logic

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

There was a small issue with the server stats not counting all record types. CPU hours may still be incorrect, but it's just an estimate anyway.

It might be incorrect due to sometimes double counting geometry optimization time + singlepoint trajectory cpu time. We will probably want to look into that in the future.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `35b63aa14e93`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.