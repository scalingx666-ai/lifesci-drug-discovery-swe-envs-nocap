# Issue

**Title:** Fix Issues #303 and #255

## Description

This PR will address issues #303 and #255. The first issue is described by the inability of the SMILES parser to read CurlySMILES as well as an issue reading bonds. The second issue is addressed by a single line. For #255, the SMILES writer has been reworked to longer be recursive and new test cases have been added to ensure that it functions properly.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `795385f39b90`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.