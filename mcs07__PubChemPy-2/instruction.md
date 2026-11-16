# Issue

**Title:** Pandas Series

## Description

Hi Matt,

I've found your PubChemPy to be very useful. I'm wondering if you would be interested in adding a `to_Series()` method to the `Compound` class. The benefit would be to allow the easy creation of pandas Series (and, by extension, DataFrames) from a list of CIDs without having to write to disk.

Not sure you'd be interested because it will add a dependency on pandas but I think the extra functionality could be worthwhile. Theres a few other bug-fixes for small things I encountered and I can split them out if you like.

best regards,
zachc p

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `431bc1861642`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.