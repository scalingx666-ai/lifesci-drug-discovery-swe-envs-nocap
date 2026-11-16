# Issue

**Title:** Fixed splitting perturboutcome by cell_line

## Description

The example mentioned in the  PerturbOutcome page (https://tdcommons.ai/multi_pred_tasks/counterfactual) does not work.

The example reads:
```
from tdc.multi_pred.perturboutcome import PerturbOutcome
data = PerturbOutcome(name = 'scperturb_drug_SrivatsanTrapnell2020_sciplex2')
split = data.get_split()
```

This raises a `AttributeError: 'AnnData' object has no attribute 'groupby'` on the line `cell_line_groups = df.groupby("cell_line")`

I think this change should fix the error.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `cd82d60a60db`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.