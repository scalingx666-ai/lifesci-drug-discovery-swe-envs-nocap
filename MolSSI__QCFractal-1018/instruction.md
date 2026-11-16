# Issue

**Title:** Use simpler/faster query for compute_history manager_name query

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

The query for records whose compute_history was computed by a particular manager was very slow. The `or` that was being used caused the query planner to not use the index on `record_compute_history`. So now the query really only searches the compute history, and the user would need to do a second query to obtain records where the `base_record.manager_name` was that manager.

On a test query, reduces the time from 47,000ms to 20ms.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b223ba3f63c7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.