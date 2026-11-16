# Issue

**Title:** Make encode_to_json work recursively

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Improves the `encode_to_json` function in `qcportal.serialization` so that it works recursively. This will allow for converting entries and specifications to plain python objects suitable for later `json.dump`.

@jaclark5 

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `49f1a146b34a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.