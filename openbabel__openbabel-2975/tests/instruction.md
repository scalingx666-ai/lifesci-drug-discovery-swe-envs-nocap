# Issue

**Title:** Fix tetrazole protonation handling in the pH model

## Description

.

This updates the tetrazole entries in data/phmodel.txt so that both graph-distinct protonated tetrazole forms are deprotonated while preserving aromaticity.

A regression test has also been added covering the four tetrazole examples reported in #2284. The test fails with the previous transforms and passes with the updated rules.

The change is based on the bug report, test cases, and proposed solution from @rubbs14 in 

The original pKa value of 4.89 from the existing tetrazole entries has been retained.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c9cca3b1e2b8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.