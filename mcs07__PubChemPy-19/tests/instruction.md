# Issue

**Title:** Allow requests with xref input

## Description

Minimal changes allowing for xref requests without breaking any tests.

I am not familiar enough with the PubChem API to know if there are any other search-types which should be treated the same way as xref.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d698fba51970`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.