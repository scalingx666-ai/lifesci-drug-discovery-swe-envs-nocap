# Issue

**Title:** Swallow stdout/stderr from qcengine to preven json parsing issues

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

This is inspired by a few reports of computational chemistry codes printing output to stdout/stderr, which messes up the (admittedly hacky) way we transfer json between a subprocess and qcfractalcompute.

This just wraps the call to qcengine in redirect_stdout/redirect_stderr, causing it to ignore any of that output

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `63f62e5b1648`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.