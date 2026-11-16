# Issue

**Title:** Give searches unique ID, use Mutex to guarantee 1 at a time

## Description

We were seeing the wrong results returned sometimes, I *think* this is because the http server is run multithreaded and it could end up doing multiple search requests at once with a single linear pipe to communicate to backend.  The Mutex in python should prevent this from happening, and I've also added a unique ID identifier for each search that should serve as a fallback to make sure incorrect results are never returned.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9786c03bcc72`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.