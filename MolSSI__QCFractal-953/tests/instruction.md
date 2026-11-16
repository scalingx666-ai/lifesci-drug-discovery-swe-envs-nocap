# Issue

**Title:** Some DB warning & shutdown fixes

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

1. Fixes a (correct) warning that we aren't passing in flags correctly to a regex (we were passing the multiline flag into the `count` parameter positionally)
2. Postgres DB was not being shutdown in snowflakes

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fd9d68bc5438`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.