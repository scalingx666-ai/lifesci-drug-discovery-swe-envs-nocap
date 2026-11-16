# Issue

**Title:** model_selection module: Group splitter

## Description

Add the sklearn GroupShuffleSplit class, which optionally can create splits based on the size of the groups, i.e. the number of samples instead of the number of groups.

This PR makes the splitter available as experimental feature in MolPipeline. However, if it's accepted and merged into sklearn we can remove this PR (or experimental feature) from MolPipeline. See the sklearn PR

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0bd34708eea9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.