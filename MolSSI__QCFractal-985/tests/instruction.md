# Issue

**Title:** Making dataset views should always include required record fields

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

When specifying fields to include (in general, but particularly when making a dataset view), the given fields will be included and everything else will be excluded (by convention). So in order to keep the default fields, users need to put a '*'.

Dataset views should include the required fields by default. Otherwise records created this way won't be usable since those required fields will be missing, raising a validation error in pydantic.

Should fix issue #984 

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `41b2e99b9ccf`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.