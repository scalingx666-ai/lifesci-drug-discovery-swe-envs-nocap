# Issue

**Title:** Fix CSV Serializer in StandaradCSVRunner

## Description

Now we actually make use of the header in order to serialize the csv correctly reading from the result.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8ee13d3a9ccc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.