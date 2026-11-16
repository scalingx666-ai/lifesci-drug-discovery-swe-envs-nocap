# Issue

**Title:** Web app: Fix crash when viewing compute history due to nested values

## Description

Provenance may contain nested objects (e.g. Psi4's module_roles), which React cannot render as a child. Render them as indented sub-lists, only show N/A for null/undefined/empty values instead of any falsy value, and allow extra fields in the ComputeHistory provenance type.

Assisted-by: claude-code/2.1.310:claude-sonnet-5-5

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66bf3238e5b4`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.