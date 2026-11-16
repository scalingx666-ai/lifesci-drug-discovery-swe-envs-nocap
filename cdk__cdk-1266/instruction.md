# Issue

**Title:** Fixes #1035 - rather than avoid using templates when we have DB stere…

## Description

…o we try the template anyways. If the double bonds happen to be correct then all is find.

This is useful for cases like porphyrins which have set double bond layouts.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dcd453efbda6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.