# Issue

**Title:** Add single loss evaluation

## Description

Close #90

The single loss evaluation is mostly analogous to the `evaluate_r2` function. 
- For each combination of drugs, cell line, and dosage we compute the output of the autoencode when presented with the true gene expression values that belong to that combination, `y_true`. 
- The r2_score is computed for each single data point/observation and not only on the mean of the obs that match the drug, dose, cell line ocmbination 
- Subsequently, we compute the mean to get one score per combination. 

Unfortunately, I overserved many -inf results, so I am excluding them to get proper scores but tracking them during the evaluation.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `66846c008330`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.