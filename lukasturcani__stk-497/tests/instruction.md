# Issue

**Title:** Add a mongo command

## Description

Makes it easier to start a MongoDB instance (which is
necessary for running all the tests). Running Mongo in
docker avoids the pain associated with setting up a local
Mongo server.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d9855609c872`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.