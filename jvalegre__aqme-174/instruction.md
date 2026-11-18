# Issue

**Title:** Temporal bug fix for calculations that fail before the first step

## Description

AQME was failing to evaluate a calculation that failed before finishing the first optimisation step due to an error in the SCRF input (read was specified but no details were added at the end). 

Details and testing files have been sent by email so they can be checked before merging.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e1762b2d352d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.