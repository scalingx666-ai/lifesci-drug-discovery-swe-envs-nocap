# Issue

**Title:** Jwilber/lepton use shared secrets

## Description

I recently learned you can use team-shared variables with Lepton: [link](https://docs.nvidia.com/dgx-cloud/lepton/features/workspace/secret/), so I created new shared variables.

This allows anyone on our team to run the workflow locally, without having to change from my vars.

I also added:
- a debug script
- flags to skip kratos/wandb
- logic for single gpu resource

To run locally:

```
python ci/lepton/core/launch_job.py --config-path="../model_convergence/configs" --config-name="recipes/debug"
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f01a9d2ea371`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.