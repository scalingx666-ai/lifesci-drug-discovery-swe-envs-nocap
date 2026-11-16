# Issue

**Title:** Calibrated probas for Conformal prediction

## Description

This PR adds a new method predict_proba_antitonic (and tests) to transform conformal p-values into well-calibrated probability estimates. This addresses the limitation of standard conformal p-values (which form prediction sets) by using isotonic regression to map them to calibrated probabilities, based on Vovk et al. (2014) ["From conformal to probabilistic prediction."](https://arxiv.org/pdf/1406.5600)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `449948798224`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.