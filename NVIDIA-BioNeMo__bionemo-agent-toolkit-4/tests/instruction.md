# Issue

**Title:** feat(kermt): add static eval definitions for the open-model skills

## Description

Expose the task-eval definitions used to measure the KERMT skills, matching the NIM skills' evals/ convention. Adds open-models-skills/kermt/evals/<skill>/ evals.json for the 6 evaluated skills (finetune, embed, continue-pretrain, add-cmim-pretrain, pretrain-scratch, infer).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `29d5444de9da`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.