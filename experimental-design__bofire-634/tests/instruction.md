# Issue

**Title:** Active Learning Strategy: fix missing input processing for acqf samples.

## Description

## Motivation

The active learning strategy crashes for mixed domains (some input features are categorical) when 

```
mc_samples = sampler.ask(candidate_count=self.acquisition_function.n_mc_samples)
# followed by 
torch.tensor(mc_samples)
``` 
gets categorical features instances as strings and complains.
While looking at the fix i think the input processing is missing in the active learning strategy. I think this was not caught during development as the utilized benchmark only has numerical features in 0-1 range. 

## Steps Taken

The missing transform was added. 

## Test Plan

Additional tests are now present. The original test passes, and the additional tests make sure the strategy works for mixed as well as purely categorical domains.  A slow test also tests for candidates actually having comparatively large uncertainties compared to average uncertainties.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b02543fae356`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.