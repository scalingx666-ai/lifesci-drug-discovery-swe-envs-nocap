# Issue

**Title:** Torsion symmetry update.

## Description

## Description
This PR allows qubekit to deduplicate torsion scans by torsion symmetry, this should lead to less torsion drives. Torsion symmetry is also used during fitting, here like torsions are linked together using parameter eval tags which should lead to faster fitting as the gradients of fewer parameters are required. The default fitting convergence criteria has also been relaxed slightly. 


## Status
- [X] Ready to go

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b49ac879618a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.