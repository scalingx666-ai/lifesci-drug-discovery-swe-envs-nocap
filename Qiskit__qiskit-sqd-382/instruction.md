# Issue

**Title:** fix symmetrized count aggregation

## Description

Fixed the ranking of sampled CI strings when ``symmetrize_spin=True`` in `qiskit_addon_sqd.fermion.diagonalize_fermionic_hamiltonian`. If the same string was sampled in both spin sectors, its alpha and beta counts were previously ranked separately rather than being added together. This could cause a lower-weight string to be retained when ``max_dim`` truncated the subspace.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f3386767e609`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.