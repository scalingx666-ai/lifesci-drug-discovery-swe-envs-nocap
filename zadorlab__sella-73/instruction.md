# Issue

**Title:** Further performance improvements and addition of PBC cell optimization

## Description

## Summary

Add unit cell optimization for periodic systems and further performance improvements to Sella's internal coordinate engine.

**Cell optimization** (`optimize_cell=True`): simultaneously optimizes atomic positions and unit cell parameters using translation-rotation internal coordinates (TRICs). Supports molecular crystals via rigid fragment mode, Niggli reduction for skewed cells, finite-difference Hessian refinement, and stress-based convergence criteria. Both internal-coordinate (`CellInternalPES`) and Cartesian (`CellCartesianPES`) variants are provided.

**Performance**: 
Key changes:
- GPU-resident Hessian update via torch CUDA (eigh, TS-BFGS, projections stay on device between steps)
- Rotation vmap batching: one JAX dispatch per fragment instead of per-axis (18–30× faster for rotation derivatives)
- SVD → QR replacement for pseudo-inverse and constraint basis computation
- `np.add.at` → `np.bincount` for sparse Hessian scatter (2.5× faster)
- Matmul reassociation throughout to avoid materializing n×n intermediates
- Extensive caching: Jacobian B matrix, basis, constraint Hessian, SparseInternalHessiansSkeleton (index-only data reused across steps), translation vectors, all_positions vstack

**Bug fixes**:
- ASE 3.28 calls `gradient_converged()` instead of `converged()` in its run loop, bypassing Sella's stress convergence check. Added override to delegate correctly.
- `get_Hc` crash when `L=None` due to floating-point non-determinism in `get_x()` — switched to byte-exact state hash for position comparison.
- Dummy atom convergence: dihedral unwrapping (modular arithmetic to avoid 2π jumps), improved h0 diagonal guess, and constraint projection via IC null-space instead of Cartesian min-norm.

### Approaches tried and rejected

Several other approaches were explored to further accelerate Sella without changing behavior. These did not work:

- **Secular equation solver** for eigendecomposition update: approximate eigenvalues weren't accurate enough for TS-BFGS, hurting convergence.
- **Iterative stepper** for the ODE: benchmarked but slower than the dense ODE path at tested system sizes.
- **Block-coordinate optimization** (alternating internal/cell steps): coupling through the Jacobian means joint optimization converges faster.
- **Rank-2 eigenvalue update**: mathematically doesn't work for the TS-BFGS update structure.
- **Separate trust radii** for internal vs cell DOF: reverted in favor of weighted `MaxInternalStep` (`wc` parameter).
- **Sparse `hessian_rdot_vecs`** in ODE: gather-dot-product approach was 9% slower than optimized flat-scatter + dense matvec at large sizes.

## Test plan

- [x] New `test_cell_optimization.py` covers CellCartesianPES, CellInternalPES, rigid fragments, gradient FD checks, Niggli reduction, and convergence
- [x] Benchmarked on 10-system suite (AJEYAQ, BEQGIN, PAPTUX, etc.), 100% convergence rate, ~2-4x faster than BFGS+Frechet baseline

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9d0892ddff50`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.