# Issue

**Title:** Aromatics

## Description

Change the handling of aromaticity to make sure it is only reinterpreted when explicitly asked. This also makes testing easier, since the reader and writer come closer to (de)serializers. The exception is the '*' element where the writer can't encode the aromaticity.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4d47729ac5e9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.