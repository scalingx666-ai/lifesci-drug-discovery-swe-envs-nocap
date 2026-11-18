# Issue

**Title:** Add `defaults` conda channel (needed for installations under Windows)

## Description

## Description
Under Windows, we cannot install `tensorflow >=2` via conda-forge. We need to add the `defaults` channel.

## Todos
Notable points that this PR has either accomplished or will accomplish.
- [x] Add `defaults` channel to
  - [x] environment file [here](https://github.com/volkamerlab/teachopencadd/blob/ds-conda-forge/devtools/test_env.yml)
  - [x] installation description via `teachopencadd` conda package: `mamba install teachopencadd -c conda-forge -c defaults` [here](https://projects.volkamerlab.org/teachopencadd/installing.html)

## Questions
None.

## Status
- [x] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `432eb5ecd8f3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.