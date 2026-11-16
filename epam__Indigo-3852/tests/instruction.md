# Issue

**Title:** #3530 call populate_compact_attribute() in formIndexTuple for PostgreSQL 18

## Description

PR #3530 adds PostgreSQL 18 support, but the backend crashes on CREATE INDEX ... USING bingo_idx. formIndexTuple() patches the FormData_pg_attribute of a template TupleDesc in place, and since 18 index_form_tuple() reads attlen, attalign and attbyval from the parallel CompactAttribute array instead, so attlen stays 0 and the index tuple is formed with a wrong size. The backend dies with "malloc(): invalid size (unsorted)" and SIGABRT.

populate_compact_attribute() flushes the change to the compact array, which is what tupdesc.c asks callers to do.

Nothing changes for 17 and older, the call sits inside the PG_VERSION_NUM >= 1800 branch.

Tested on indigo-1.45.0 with this branch's changes applied, built against postgresql18-devel 18.6 on AlmaLinux 8 and run on PostgreSQL 18.6. In bingo/tests, pytest --db postgres goes from 31113 passed / 3039 errors to 34152 passed / 0 failed, which is the same count as 14 to 17 give.

Base branch is add_postgresql_18 on purpose, so that #3530 picks it up directly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8abc2a65420f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.