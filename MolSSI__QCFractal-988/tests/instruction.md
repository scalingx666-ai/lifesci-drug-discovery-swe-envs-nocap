# Issue

**Title:** Improve errors for exporting to qcschema with missing data

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Requested in #950. This adds a more descriptive error message (and possible solution) if exporting a record to QCSchema that is not connected to a client, but also needs to request data.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4b1b0feadcd7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.