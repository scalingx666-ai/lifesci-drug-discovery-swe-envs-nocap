# Issue

**Title:** Extras field of records should not be None/NULL

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
The `extras` field of `base_record` (therefore all records) should probably not be null. It's more consistent that it's a dict, even if it's empty.

The original idea is that `extras` is only populated on record completion. But
  * At some point, we might make these settable by the submitter
  * We may eventually move to an EAV table, which would always result in an empty dict anyway

This inconsistency has caused problems for some users as well:  

Relatively easy fix - make the db column not null, and the pydantic field not optional. A small validator is added to halp newer clients use older servers.

This is backwards compatible - new clients can use old servers, and old clients can still use new servers.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e9bab84e6af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.