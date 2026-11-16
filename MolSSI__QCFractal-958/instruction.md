# Issue

**Title:** Force compute tag to be lowercase when modifying records

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

When modifying records (including through datasets) an exception was raised if the new compute_tag wasn't all lowercase. This was caught by a constraint on in the DB - but we should really handle it higher up.

This should force the new compute tags to be lowercase at the boundary of the web API.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `65e539d5a5c8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.