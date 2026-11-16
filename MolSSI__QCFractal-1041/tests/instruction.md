# Issue

**Title:** Better handling of stdout/stderr with errors

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

See issue #1026 

Some stdout/stderr information can be kept inside the "extras" dictionary of an errored calculation. Move this to the top level for better discoverability.

There is also a script to go through and convert all the old errored records as well, and can be done on a live server. This was a relatively recent change to QCEngine/QCElemental so there aren't that many, but the script has to go through all errored records.

## Status
- [x] Code base linted
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a32b9df8657c`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.