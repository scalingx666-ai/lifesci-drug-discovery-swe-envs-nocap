# Issue

**Title:** Fixed a bug and update references in ranged_logAUC

## Description

Previously, the ranged_logAUC was calculated firstly by taking the logarithm of the False Positive Rate (FPR), and then taking the intercept of logFPR. This could result in NaN when FPR is 0. The updated version takes the intercept first, which prevents the FPR =0 from happening and then is followed by taking the logarithm. 

The reference is also updated to the lastest manuscript that has detailed explanation of ranged_logAUC.

test cases can be seen in PR #152

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `09ad3d891183`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.