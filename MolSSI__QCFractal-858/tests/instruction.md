# Issue

**Title:** Pin pyjwt & enable invalid subject handling

## Description

## Description

An update to pyjwt enforces the standard that subjects of the JWT are strings. We use integers (ids).

So the fix:
1. Move to using strings (just stringified int)
2. Add a handler to return that the token is expired if the validation in pyjwt fails with InvalidSubjectError.
3. That exception only exists in pyjwt 2.10.0 and above, so pin that version.

Only affects servers, not clients. Upgrading a server should be transparent to clients.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `99e7b8253429`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.