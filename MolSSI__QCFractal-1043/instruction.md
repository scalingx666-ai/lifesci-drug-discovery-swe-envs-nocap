# Issue

**Title:** Add ability to rename API tokens

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

The name of API tokens is the only thing that is modifiable - expiry, scope, etc, are set at creation and not changeable.

This adds the ability to do that, with proper checks on duplicate names, etc.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `51daeea0552d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.