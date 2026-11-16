# Issue

**Title:** Make clients handle transient errors even more

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

I had some managers/clients exit when our instances went down for maintenance. This wasn't supposed to happen, but there were some gaps is how transient errors were handled. Particularly, our reverse proxy (traefik) responds with different error codes than if you were connecting to the flask/waitress endpoints directly.

This PR closes those gaps, making managers and clients even more robust to server downtime or transient network errors.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dadd3e339d76`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.