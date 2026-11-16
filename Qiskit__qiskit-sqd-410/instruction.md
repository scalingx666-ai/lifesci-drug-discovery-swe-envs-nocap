# Issue

**Title:** Fix orbital rotation antisymmetry and in-place k_flat optimization

## Description

.

### Summary

This PR fixes two bugs in orbital optimization (`qiskit_addon_sqd.fermion`):

1. **Bug 1: `_antisymmetric_matrix_from_upper_tri` was not anti-symmetric for `norb >= 4`**
   - Previously, the function populated the upper triangle using `jnp.triu_indices(k_dim, k=1)` with `k_flat` and the lower triangle using `jnp.tril_indices(k_dim, k=-1)` with `-k_flat`.
   - For `k_dim >= 4`, the row-major ordering of `tril_indices` differs from the transpose of `triu_indices` (e.g. for dimension 4, entries at `(2, 1)` and `(3, 0)` are transposed relative to `(0, 3)` and `(1, 2)`). As a result, `K[j, i] != -K[i, j]`, so `expm(K)` was not orthogonal, and `rotate_integrals` altered the Hamiltonian spectrum (e.g., shifting the FCI energy of H2O by +6.65 mHa).
   - Fix: Construct `upper = jnp.zeros((k_dim, k_dim)).at[jnp.triu_indices(k_dim, k=1)].set(k_flat)` and return `upper - upper.T`, guaranteeing exact anti-symmetry for all dimensions.

2. **Bug 2: `_optimize_orbitals_sci` did not update `k_flat` in place**
   - In `_optimize_orbitals_sci`, `k_flat -= prev_update` was performed with `prev_update` being a JAX array resulting from `_SCISCF_Energy_contract_grad`.
   - Because `prev_update` was a JAX array, Python did not perform an in-place mutation on the NumPy array `k_flat`; instead, it rebound the local variable name `k_flat` inside `_optimize_orbitals_sci`. The caller's array was never updated, causing `optimize_orbitals` to silently return the initial `k_flat` despite non-zero gradients.
   - Fix: Convert `grad` to a NumPy array via `np.asarray(_SCISCF_Energy_contract_grad(...))` so that `prev_update` remains a NumPy array, allowing `k_flat -= prev_update` to update `k_flat` in place.

### Tests

- Added `test_antisymmetric_matrix_from_upper_tri` parameterized over `norb` in `[2, 3, 4, 5, 6]` to verify that `K == -K.T`, `expm(K).T @ expm(K) == I`, and the upper triangle entries match `k_flat`.
- Added `test_rotate_integrals_preserves_fci_spectrum` to verify that `rotate_integrals` preserves the exact FCI ground state energy to machine precision for `norb = 4` (where it previously shifted the spectrum).
- Added `test_optimize_orbitals_updates_k_flat` to verify that `optimize_orbitals` and `_optimize_orbitals_sci` update `k_flat` in place when the gradient is non-zero, tested with both CI strings and bitstring matrices, as well as checking `ValueError` handling for mismatched parameter lengths.
- Added release note via reno.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `146e60468217`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.