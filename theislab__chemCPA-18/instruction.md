# Issue

**Title:** Add a `environment.yml`

## Description

This allows us to setup working environments via `conda env create` (or better `mamba env create`).

Later we can add the dependencies for all embedding models like so:
```yml
pip:
  - git+github.com/wengong-jin/hgraph2graph@master
```

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `0627239166de`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.