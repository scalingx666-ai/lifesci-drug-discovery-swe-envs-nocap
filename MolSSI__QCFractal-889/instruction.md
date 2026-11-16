# Issue

**Title:** Jitter for manager heartbeats and updates

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Adds options for adding jitter to manager heartbeats and updates. This does two things - helps with some random errors related to TCP keepalive, and also prevents the thundering herd effect where lots of managers started at the same time will all try heartbeat/update at the same time as well.

In addition, this PR disables keepalive connections for certain manager requests that are expected to be infrequent.

Heartbeat frequency jitter is controlled by the server, while update frequency jitter is set in the manager config.

Changes in this PR are backwards & forwards compatible.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d2c9c8316a81`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.