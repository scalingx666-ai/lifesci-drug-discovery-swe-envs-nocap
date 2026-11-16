# Issue

**Title:** Remove duplicate bookkeeping in flask storage socket

## Description

## Description
<!-- Thank you for your contribution! -->
<!-- Provide a brief description of the PR's purpose here. -->

The flask storage socket object (which holds per-flask-app qcfractal storage sockets) stored the socket in both a dictionary and in the app's extensions. No need to do both, so remove the dictionary.

## Status
- [X] Code base linted
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b963bfe89170`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.