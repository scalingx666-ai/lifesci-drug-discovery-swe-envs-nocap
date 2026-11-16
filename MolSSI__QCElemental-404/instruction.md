# Issue

**Title:** Fix typing of FailedOperation input_data in v12 model

## Description

<!-- Thank you for your contribution! -->

## Description
<!-- Provide a brief description of the PR's purpose here. -->

Since `input_data` can be a dictionary with numpy arrays, it needs to be typed with GenericData to properly handle serialization.


## Changelog description
<!-- Provide a brief single sentence for the changelog. -->

## Status
<!-- Please `bash scripts/format.sh` in the base folder or use pre-commit. -->
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09eb992f81e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.