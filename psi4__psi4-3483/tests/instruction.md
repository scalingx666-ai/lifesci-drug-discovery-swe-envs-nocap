# Issue

**Title:** Don't allocate exchange-Hessian intermediates for pure functionals

## Description

## Problem

`DFJKGrad::compute_hessian()` unconditionally allocates the exchange (K) intermediates `dAa_ij`, `dAb_ij`, `dea_ij`, `deb_ij` — each `3*natom * naux * nocc^2` doubles — regardless of whether exact exchange is present, and allocates the beta copies even for a restricted reference. Their *uses* are already guarded by `do_K_` / `!same_ab`, but the allocations are not. Since `Matrix` zeroes its storage on construction, these buffers are **committed** (touched), not merely reserved.

For a **pure functional** (`do_K_ == false` — every non-hybrid GGA/meta-GGA: PBE, TPSS, SCAN, r²SCAN, M06-L, …) this is several GB of memory the run never reads:

| system | wasted allocation (4 buffers) |
|---|---|
| benzene / def2-SVP | ~0.17 GB |
| naphthalene / def2-SVP | ~1.8 GB |
| caffeine / def2-SVP | ~6.6 GB |

On a memory-limited machine this drives the process into swap. A caffeine/def2-SVP pure-meta-GGA Hessian on an 8 GB machine spent hours thrashing on ~6.6 GB of dead buffers.

## Fix

Guard the allocations by `do_K_`, and the beta copies by `!same_ab`. Every use of these pointers is already under the same conditions, so they simply stay `nullptr` when unused. Hybrid UKS is unaffected (all four still allocated); hybrid RKS additionally drops the redundant beta pair.

## Validation

- **Numerically inert.** Single-threaded (deterministic) TPSS/def2-SVP analytic Hessian, with vs without the change: **bitwise identical** (`max|Δ| = 0`), energy identical to 12 digits. The change only skips allocating buffers that are never read.
- **Memory.** Confirmed the buffers are the dominant Hessian allocation and scale as `4 * 3*natom * naux * nocc^2`; removing them for a pure functional recovers the full amount above.
- **Guards audited** across all use sites (the deriv-1 (A|mn) loop, the (A|B) loop, and the final K-Hessian contraction): alpha buffers used only under `do_K_`, beta only under `do_K_ && !same_ab`.

The exchange Hessian path itself (hybrids) is unchanged.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5119521a774f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.