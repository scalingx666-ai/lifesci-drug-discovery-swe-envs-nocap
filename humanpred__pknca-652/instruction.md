# Issue

**Title:** fix: interval_add_secondary() aborts when ref_id would merge intervals

## Description

Reference rows that carry more than one interval_id (two intervals sharing a window and groups) were all renamed to ref_id, silently merging them. The function now aborts with pknca_error_secondary_ref_ambiguous_spec and names the identifiers found.  Rows without an identifier still join the one identifier the other rows have.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7496f6334b63`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.