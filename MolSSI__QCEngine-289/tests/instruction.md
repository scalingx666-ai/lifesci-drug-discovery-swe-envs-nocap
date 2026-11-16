# Issue

**Title:** Added basic harness for TeraChem Protocol Buffer Server mode.

## Description

## Description
Added a basic `ProgramHarness`  for TeraChem's "server mode".

## Changelog description
Added a basic `ProgramHarness`  for TeraChem's "server mode".

## Status
<!-- Please `pip install .[lint]; make format` in the base folder. -->
- [ x] Code base linted
- [ ] Ready to go

Given this is my first PR please let me know what else your team would like to see! I'm trying to get an MVP version up and working so the code you see is rather minimal. The underlying library for communicating with the server--`tcpb`--needs a little love. I'll be patching it up to have better error handling over the coming weeks and intend to expand this `ProgramHarness` to reflect these changes once made.

Let me know what else your team would need! I'm happy to leave this PR open until a more robust harness is built (a couple of weeks, most likely), but I wanted to get eyes on as soon as possible. Thanks!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `43639f21ac3d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.