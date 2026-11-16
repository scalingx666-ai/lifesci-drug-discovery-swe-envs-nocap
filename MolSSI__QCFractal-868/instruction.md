# Issue

**Title:** Add extra compute route for information (for logging)

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

Right now, compute workers get info from the server via `/api/v1/information`.  This PR allows managers to contact `/compute/v1/information` instead. This allows for cleaner metrics between general API usage and compute workers. Old managers can still be run as the `/api/v1/information` endpoint will still be available.

NOTE: default roles have changed (new API route added to the "compute" role), so there is a tiny migration adding the those permissions.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `1e8efc67436d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.