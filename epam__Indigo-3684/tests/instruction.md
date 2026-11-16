# Issue

**Title:** fix SMARTS search in Postgres

## Description

- [x] PR name follows the pattern `#1234 – issue name`
- [x] branch name does not contain '#'
- [x] base branch (master or release/xx) is correct
- [x] PR is linked with the issue
- [x] task status changed to "Code review"
- [x] code follows product standards
- [x] regression tests updated

This patch  - a PostgreSQL regression introduced in PR #3154 for indexed molecule SMARTS searches. The regression came from treating SMARTS like the cursor-backed exact/gross/mass paths and calling `finishOnTransactionEnd()` in `_prepareSmartsSearch()`. 
Unlike those search types, molecule SMARTS reuses the substructure preparation path and never creates `_searchCursor`, so the added deferred-finish call could only fail there. Molecule substructure is unaffected because it calls `_prepareSubSearch()` directly, and reaction SMARTS is unaffected because the analogous reaction code never added the deferred-finish call.

To lock that behavior down, the new pytest coverage builds a dedicated molecule table and forces bingo_idx usage with enable_seqscan = off, then verifies both the plan shape and the returned IDs for exact, substructure, and SMARTS

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3ea44bea7b63`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.