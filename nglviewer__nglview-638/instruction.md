# Issue

**Title:** add ipywidgets to install_requires

## Description

+ pyzmq works fine with
    - centos 5: binary install
    - macos: it will be installed from source code, quite quick.

+ also add `test_movie_making.ipynb`.

cc @jbarnoud #632

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a2cd1070da74`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.