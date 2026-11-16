# Issue

**Title:** Check if native files has been set before fetching

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
This adds a check to differentiate `BaseRecord.native_files_` being None because there really aren't any (vs there are, but not fetched yet).

Should help with #950 

## Status
- [X] Code base linted
- [ ] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0141ee9314cb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.