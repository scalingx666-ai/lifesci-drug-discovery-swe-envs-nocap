# Issue

**Title:** Performance improvements

## Description

Major rewrites and vectorization of key steps in Sella, focusing on order=0, internal=True. This included vectorizing loops, caching matrices, and reducing unnecessary operations. Only the final swap of RFO to QuasiNewton should have any affect on outputs and in testing this was found to be minimal. @juditzador I don't understand why RFO was the default choice before, hoping you can shed some light on that.

In my testing on optimizing a 50 atom metal complex with OMol-eSEN-sm-cons, 10 optimization steps was reduced from 80-90 seconds to 3.7 seconds.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c8a071c3cb0f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.