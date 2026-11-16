# Issue

**Title:** Analyze errors

## Description

Clarify the "error types" reported in `Python/check_mof_linkers.py`, `smiles_diff.py` and related scripts, closing #7.  This PR also established an Analysis subdirectory containing plotting code and digging into the root causes of some of the apparent mismatches between a GA/ToBaCCo "recipe" and the MOFid calculated from the MOF.

More work will be necessary to clean up `Analysis/plot_round_trip_errors.R` and decide on the best figure(s) to show the success rate and causes of mismatch in the paper.  Until then, I am going to merge this code so I can go ahead and more easily proceed with #6 and some of the other action items that remain.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a5107d747389`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.