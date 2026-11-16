# Issue

**Title:** Fix minor bugs on current `dev/mfbo` branch

## Description

This PR fixes two minor bugs on the `dev/mfbo` branch that have not been detected previously resp. have probably been included during the previous rebase process.
1. `comp_df` of `CategoricalFidelityParameter` did not set the index correctly: Previously, the code did not set the index at all when creating the computational representation, failing with the following error when trying to call `.transform`: `ValueError: You are trying to merge on object and int64 columns for key 'Labels'. If you wish to proceed you should use pd.concat`. This has now been fixed in 6f4ddf328718eaf6112461f9d473a16d55fc7c55 and corresponding tests for all types of fidelity parameter have been added in 9fcd0b55ec8c5cd7d0d122b7df4c78bfa3d8c4f9
2. There was still an old import of `DTypeFloatNumy` which did not use the `active_settings`. This was already identified in one of the follow up PRs, but I decided to already include this now as I wanted to have a clean `dev/mfbo` branch. This has been fixed in 84fb01aa6ca907d38e38e6bc3c4a6347d5b92a99.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b868d67e0095`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.