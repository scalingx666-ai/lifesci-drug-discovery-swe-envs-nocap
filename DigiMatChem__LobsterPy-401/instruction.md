# Issue

**Title:** Fix ICOHPDistance plotter

## Description

Incase on Non orbital resolved ICOHPLIST / ICOOPLIST / ICOBILIST files, icohp distance plotter failed with TypeError as dict is None in such case.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5386931e3cbc`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.