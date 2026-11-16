# Issue

**Title:** Added back new parameters to standardize_relations() which somehow go…

## Description

When Jessica transferred the changes from the curation_funcs branch to a new curation_funcs_14 branch, she included the changes in the body of the data_curation_functions.standardize_relations function, but missed the 'def' line which specified some new optional parameters; therefore the function failed to run, because the parameters weren't defined. This fix should be included in the 1.4.2 release.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0540120e3a03`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.