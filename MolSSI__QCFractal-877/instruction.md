# Issue

**Title:** Option to shut down managers if idle for too long

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->
(builds on PR #876)

Sometimes, we would like managers to shut down if they are not running any jobs for too long. This is particularly true if managers themselves are submitted as jobs to a queuing system.

This PR adds the functionality to specify a maximum idle time in the manager config: `max_idle_time`. This time is approximate, as idleness is only checked at the time a manager fetches new tasks from the server.

If at update time the idle time is beyond the configured max, the manager will stop itself.

Because of PR #876, this can also be specified as a string: `60s` or `30m`, or with colons (`30:00` being 30 minutes).

@j-wags 

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f5b076e3b5b6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.