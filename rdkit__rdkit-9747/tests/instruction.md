# Issue

**Title:** Github9744 synthon shape search hit order

## Description

#### Reference Issue

#### What does this implement/fix? Explain your changes.
Implemented a new function for removing duplicate synthon combinations from hit sets.  The new method doesn't sort the potential hits so that the input order is preserved.  The upshot is that potential hits for shape searches now come out in descending order of approximate similarity as the other searches do.

There should be a marginal improvement in speed because there is now only ever 1 sort of potential hits rather than the 2 done previously.

#### Any other comments?

I have also updated some of the expected results in the LONG_TEST_catch_tests.cpp which hadn't kept up with the recent conformer generator improvements.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `73268ba001e8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.