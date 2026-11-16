# Issue

**Title:** CI: allow manual dispatch of QP Configuration

## Description

Scheduled workflows are disabled by GitHub when the repository has no activity for 60 days. That happened to master in August 2026: the Saturday QP Configuration runs stopped, the qp2-config cache they maintain expired, and QP Compilation on dev-stable (and master) has failed since 2026-08-27 at the final configure with 'ZeroMQ (zeromq) is not installed'.

Adding a workflow_dispatch trigger so the cache refresh can be run on demand (and again next time the schedule is disabled by the inactivity rule).

This PR also triggers QP Configuration immediately, rebuilding the stale cache.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0968e4d30053`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.