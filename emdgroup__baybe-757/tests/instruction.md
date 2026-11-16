# Issue

**Title:** Botorch preset

## Description

DevPR, parent is #745 

Adds the `BOTORCH` preset for GPs. 

### Important information
* I think it's critical to actually assert that the preset exactly recovers the BoTorch behavior, in the form of a test, for mainly two reasons:
  1. The construction involves quite a few things to be configured, i.e. handling both singletask/multitask (the latter even requiring a new custom gpytorch module), setting all sorts of priors correctly, etc. Blindly believing that everything is correct and then just claiming `this is the BoTorch behavior` seems like a bad idea. The test ensures this explicitly.
  2. It also as an automatic alert mechanism for all situations when something is changed on the BoTorch side, informing us about breaking changes that yield different behavior but are not fully documented (which happened already several times).
* I've also invested quite some effort to test the new multitask mean logic, i.e. that it not only recovers the BoTorch logic but that it also fills *one* of the missing gaps that will ultimately make our transfer learning model *truely scale-invariant* w.r.t. the different input tasks. In particular, I made sure that the only missing piece is the noise model stratification, which should be added in a follow-up PR and is the analogous to the stratification over means shipped by this PR. (This explains the changes to the streamlit script.)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `4f89af4546b1`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.