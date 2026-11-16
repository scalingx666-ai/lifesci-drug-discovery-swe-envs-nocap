# Issue

**Title:** Add getting dataset status by compute tag

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Adds a function (client & server) to get the status of a dataset grouped by tag.

Tested with some larger datasets on a test server and it seems fast enough (typically less than 3 seconds or so)

(if there's any more, I imagine we should make one general function)

Requested by @jaclark5 

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a22973c55a78`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.