# Issue

**Title:** More intuitive log dir

## Description

Instead of:

`{log_dir}/logs_{agent_name}_{timestamp}`

Have:

`{log_dir}/{experiment_name}_{agent_name}_{timestamp}`

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `64b2e07a789a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.