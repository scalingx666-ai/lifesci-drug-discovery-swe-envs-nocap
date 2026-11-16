# Issue

**Title:** Fix XC force when only some atom groups have a NLCC

## Description

`atomic_density_form_factors` always produces the form factors for all atom groups, so simply filtering out the atom groups without an NLCC leads to an index mismatch between the atom group and the form factors. For example if atom group 1 has no NLCC and atom group 2 has one, then the force computation for atom group 2 would use the form factors of group 1. Even worse, since the atom group order differs between MPI ranks, the force could be different across MPI ranks.

This PR simply fixes this by first finding the indices of atom groups with an NLCC, and then filtering both the atom groups and the form factors. I verified that this works with CUDA.

It also makes the order of the atom groups deterministic by preserving the order of the atoms.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `94ec5610ab88`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.