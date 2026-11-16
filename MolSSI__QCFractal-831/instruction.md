# Issue

**Title:** Add internal job to delete old access log entries

## Description

<!-- Thank you for your contribution! -->

## Description
Adds an internal job to periodically delete old access logs. The retention period is configurable, but the default is to keep all log entries forever.

The job will run daily

## Changelog description
Add internal job to delete old access logs

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `56b9189fe8be`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.