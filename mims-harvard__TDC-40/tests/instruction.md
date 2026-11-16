# Issue

**Title:** Drugsyn benchmark group

## Description

There are two splits:

- one is by metric (css, loewe, zip, bliss, hsa)
- the other is by tissue type (cell lines can be grouped into 9 tissues

Also added code to the base benchmark class for dealing with pickle files instead of csv

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dbf9084926bb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.