# Issue

**Title:** Attempt at autoreset fix, but add more logging

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Some records have a large number of auto-resets - beyond the limits set on the server. The reason is unclear - the logic in `should_reset` appears good.

 This attempts a quick fix, but also adds more logging to see if we can track it down if it is not fixed.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3a180304a4c2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.