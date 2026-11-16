# Issue

**Title:** Created a conda environment file for easy setup

## Description

I created a file called `environment.yml` that contains all of the requirements that sella requires to run. This is simply for easy installation of sella for conda users. The modules required are as follows

  - python >= 3.5
  - scipy >=1.1.0
  - cython
  - ase

Let me know any questions or concerns.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8a38ae20c611`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.