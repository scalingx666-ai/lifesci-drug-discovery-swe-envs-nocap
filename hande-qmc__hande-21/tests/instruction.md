# Issue

**Title:** Take Diagonal Copying Out of IP-DMQMC Test To Enable IP-DMQMC With Replica Tricks

## Description

Hi.

I think copying of diagonal Hamiltonian elements across replicas in `annihilation.f90` should be put out of the IP-DMQMC test, otherwise if we enable `replica_tricks` in IP-DMQMC diagonal energy contribution of the second replica (`psip_list%dat(2:nspaces, idet)`) would be undefined.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `42239cf36d4e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.