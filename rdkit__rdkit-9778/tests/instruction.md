# Issue

**Title:** Fix a couple of MHFP bugs

## Description

1. There was a mismatch between the default value of the kekulize parameter between C++ and Python. I updated all of them to have `kekulize=false`. This is what the C++ code has been doing and what the explicit default on the Python code was, this clears up one set of changes that I missed while fixing #3942.
2. MHFP fingerprints were order dependent. I added a step to canonicalize the atom ordering before generating the FPs. These FPs are computationally expensive enough that this shouldn't have a noticeable impact on performance.

Both bugs were reported by Andrew Dalke

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `01976e53e9a1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.