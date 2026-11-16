# Issue

**Title:** Add identify_non_dominated_configurations

## Description

Adds `identify_non_dominated_configurations` to `Objective` and `Campaign` to identify target configurations on the Pareto front.

When called via `Campaign`, the user can set the flag `consider_campaign_measurements`, to either in- or exclude the campaign measurements for the computation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `7f8246f8bace`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.