# Issue

**Title:** Allow for manual specification of snowflake host

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
Sometimes you may want to bind a snowflake to a different IP/host. I have heard that on Windows, the WSL may choose a  different IP for localhost (where I had hardcoded `127.0.0.1`).

This allows you to bind to a different host/ip. It also changes `127.0.0.1` to `localhost` for the default.

@sjayellis maybe this will help

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c5162bc994ec`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.