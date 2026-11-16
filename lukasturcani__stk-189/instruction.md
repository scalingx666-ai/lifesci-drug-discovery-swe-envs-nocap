# Issue

**Title:** Deprecate ValueMongoDb arguments.

## Description

This PR replaces the single `lru_cache_size` argument with two separate `cach_size` arguments. This has the benefit of allowing the user to toggle each cache individually. For example, you might want to allow caching for the `put` method, while preventing caching for the `get` method. You might want to prevent caching in the `get` method exclusively in cases where you are adding the same molecule to the database, but in each case it has a different position matrix. In such a situation, the `get` method would not reflect the updates to the database if caching is turned on.

This PR also makes the tests use an actual MongoDb for testing - because it is easier to test than using a Mock database.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `ebf876d52070`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.