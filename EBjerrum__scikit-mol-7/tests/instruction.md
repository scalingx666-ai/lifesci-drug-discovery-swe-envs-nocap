# Issue

**Title:** RDkit 2d descriptor transformer

## Description

By default, it collects all the possible descriptors and calculates all, transforms as np array. 
There is a callable function get_desc_names(), so the users can confirm which descriptors were computed.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `54e34524cea3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.