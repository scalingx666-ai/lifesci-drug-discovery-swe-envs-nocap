# Issue

**Title:** Add key protection while searching

## Description

This will allow databases to have passwords associated with them, and to not perform searches unless the password has been passed.

To do this we had to get rid of the notion of 'all', and allow searches to pass the specific database names (plural) and keys (plural) as comma separated form values.

Security note:
In production the frontend should be hitting an endpoint on the frontend server that should have a middle layer submitting the requests with the passwords, as the passwords should not be exposed to end users at all.  Should *always* be over https.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b84e217310d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.