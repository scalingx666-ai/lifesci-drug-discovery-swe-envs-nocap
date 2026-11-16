# Issue

**Title:** Caching fix

## Description

MongoDb's caching of `_put()` was not working, because `insert_one()` modified the `HashableDict` which was placed in the `lru_cache`. This resulted in the `HashableDict` in the `lru_cache` being different to the a clean `HashableDict` passed to `_put()`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5967e8c0e888`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.