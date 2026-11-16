# Issue

**Title:** Serenity: Geometry Optimization

## Description

In this PR, I also added the feature to my parser that it raises an error when there are multiple different systems in the output file. Serenity often uses multiple systems, but after looking at the ADF parser and the v2 paper, I have decided to postpone the handling of this to the v2 parser. I hope this is acceptable.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e0082a671634`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.