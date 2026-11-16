# Issue

**Title:** Metrics review, CDISCOVERY 278

## Description

This PR fixes a bug that caused an NaN to result from modelability metrics (physchem and bioactivity), and also makes updates to the plots for the metrics. All plots have been tested in a notebook and are expected to work in the plotting script. However final results will be tested when the embedding generation finishes for the bioactivity metric.

The following items remain:
- [ ] test plotting once bioactivity embedding generation completes
- [ ] Examine issue with low uniqueness value to ensure it does not result from a bug

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `463bdf02ba9f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.