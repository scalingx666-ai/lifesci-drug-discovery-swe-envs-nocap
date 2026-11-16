# Issue

**Title:** Fixed bug in reset logic caused by dictionary comprehension

## Description

## Description
Our server had auto_reset for failed jobs set to a maximum of 5 retries for all error types. I discovered that qcfractal was continuously resetting my failed jobs (I eventually manually canceled them after they were attempted >1600 times). This was occurring because of line 56 in ~/qcfractal/qcfractal/components/tasks/reset_logic.py :

error_counts = {error_map.get(k, "unknown_error"): v for k, v in error_counts.items()}

This dictionary comprehension overwrites the count when there are multiple error types mapped to a single general error category. The unique_errors set defined on line 48 was correctly accumulating errors, but since set ordering is deterministic within a python process, the comprehension discarded all but one of the error types consistently, each time should_reset was called. In my case I had 1 BadStateException and 1616 TooManyJobFailuresError. While all errors were being captured, only the BadStateException would have triggered should_reset to halt.

I added a fix and a testcase.

## Status
- [ x ] fixed bug
- [ x ] added representative testcase
- [ x ] bug fails test, fix passes test
- [  ] ran full test suite

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c332ec0ee980`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.