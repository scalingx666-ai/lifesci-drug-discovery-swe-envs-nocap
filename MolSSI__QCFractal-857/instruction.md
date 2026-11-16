# Issue

**Title:** Add option for opt-in usage tracking for Parsl

## Description

## Description

Parsl contains an option to enable the Parsl team to collect statistics regarding Parsl usage. This collection and tracking is  is <ins>**opt-in**</ins>.

This PR adds an option to the manager config to set the usage data tracking level for data sent back to the Parsl team.

By default, the tracking is disabled (level = 0).

For more info about what is collected & the rationale for collection, see https://parsl.readthedocs.io/en/stable/userguide/usage_tracking.html

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d9a6cba67f2c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.