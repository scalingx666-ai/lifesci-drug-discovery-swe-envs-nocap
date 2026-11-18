# Issue

**Title:** CI: Revert Win Py3.9 back to Py3.8; pin `tensorflow`<=2.6

## Description

## Description
While looking into the `tensorflow` issue reported in  I noticed that we are running the CI for Windows under Py3.9 although we intended to run all platforms by default under Py3.8 (plus an additional test for Py3.9 under Linux).
I introduced this discrepency when I made a CI test run for Win Py3.9 and forgot (?) to revert back to Py3.8:  (the exact commit: )

Pin `tensorflow` version matching the API used in T021 and T022 (i.e. 2.6).

## Todos
- [x] Revert CI back to Win Py3.8
- [x] Pin `tensorflow` <=2.6

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6dd66531462b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.