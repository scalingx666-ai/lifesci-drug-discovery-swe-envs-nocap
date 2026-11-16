# Issue

**Title:** add support for .sdf.gz files

## Description

Since the RDKit supports reading from streams, it's easy to allow FPSim2 to read directly from `.sdf.gz` files.

I also renamed `get_mol_suplier` to `get_mol_supplier`. If this wasn't an unintentional typo or you don't want to change the name of a public API function let me know and I'll remove that part of the PR.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `673bad1425d0`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.