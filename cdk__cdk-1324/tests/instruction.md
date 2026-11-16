# Issue

**Title:** Pattern.findSubstructure Javadoc names DfPattern as the default

## Description

Pattern.findSubstructure returns a DfPattern, but its Javadoc still names VentoFoggia as the default. This corrects the description and the @see tag; there are no code changes. Raised in the review of #1323.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f53632f48658`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.