# Issue

**Title:** Improve performance of task claims by managers

## Description

## Description

We've noticed that with large databases, the time to claim tasks is a bit slow (multiple seconds). This is particularly noticeable in Issue #850 .

This PR aims to improve this significantly via two main ways:

* Improving the SQL query. Not the task queue has an `available` column which can be used to filter, rather than the `status` column of the joined `base_record` table. This seems to be the fastest way, although it denormalizes stuff a bit
  * I tried a conditional `WHERE status = 'waiting'` index on base_record but that didn't even help as much
* Improving the task specification generation (which happens sometimes when claiming) so that data is retrieved in fewer SQL queries. Also, I eliminated creation of pydantic objects here, which also trims a bit of time.

Tests on a copy of a production database show a reduction from ~2-3 seconds to 0.5-0.7 seconds for 200 tasks. Getting it much lower is going to be tough, since some of that is data transfer overhead over the internet.

Note that this does require a database migration with the `upgrade-db` subcommand.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6e4aef6e49a9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.