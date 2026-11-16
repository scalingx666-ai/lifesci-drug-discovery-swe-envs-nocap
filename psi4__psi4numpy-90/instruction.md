# Issue

**Title:** added spin adapted UMP2 to psi4numpy

## Description

## Description
Adds an example spin adapted UMP2 code to psi4numpy. I ran into a few glitches learning how to spin adapt MP2 and CCSD, and would have liked to have a reference code to compare notes against. So, this PR is intended to fill that gap. 

## What are your new additions? Please provide a brief list.
* **New Features**
  - [x] New spin adapted UMP2 code example.

* **Changes**
  - [x] Add UMP2_Spin_Adapted.py  

* **Questions**
    I'm not sure if the style is up to snuff, so I'll change anything that is noted.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `61457dc6c375`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.