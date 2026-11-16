# Issue

**Title:** Speed up the three-body dispersion gradient for molecules

## Description

In the molecular (non-periodic) branch of `atm_gradient_latp`, the pair quantities (distances, `1/r`, damping terms and `sqrt(C6)`) are now computed once per atom pair in four shared symmetric matrices. For each atom pair, an inner SIMD loop over `kat = 1, nat` reduces the pair's scalar edge weights in registers without square roots, powers or 3D updates. Each thread accumulates the pair contributions into heap-allocated `O(N)` copies of `energies`, `gradient`, `sigma` and `dEdcn` and sums them once in a critical section (#1350), keeping OpenMP stack usage bounded with no thread-local `N^2` allocations. The OpenMP loops keep main's `collapse(2) schedule(dynamic, 32)`. The periodic branch and the GPU path are unchanged.

| Case | main | this PR | Time saved |
| :--- | ---: | ---: | ---: |
| Geometry optimization, remdesivir (77 atoms), 1 thread | 6.95 s | 6.67 s | 4% |
| Geometry optimization, remdesivir (77 atoms), 4 threads | 4.14 s | 4.06 s | 2% |
| Gradient, cyclosporin A (196 atoms), 1 thread | 1.03 s | 0.91 s | 12% |
| Gradient, cyclosporin A (196 atoms), 4 threads | 0.52 s | 0.48 s | ~3–8% |
| Gradient, LNCI16 2xHB238 complex (538 atoms), 4 threads | 11.19 s | 11.34 s | ~0% |

Differences below about 3% are within run-to-run spread, and the 4-thread cyclosporin and 538-atom cells varied by up to 17% between runs. The gain holds with LTO: GCC can't inline `deriv_atm_triple` into the OpenMP region without it, but with `-Db_lto=true` on both builds the cyclosporin gradient still drops from 0.87 s to 0.76 s (12% saved).

Results agree with main to round-off, not bitwise, because pair terms are factored out of the triple products. Cyclosporin A energies match main to all 12 printed decimals and 1-thread gradients agree to 1e-18 Eh/bohr; the remdesivir optimizations take the same 50 steps to the same energy; on the 538-atom complex at 4 threads the gradient agrees to 1e-14 Eh/bohr.

**Trade-offs:** the four shared pair matrices add `4 x N^2` doubles (about 9 MB for 538 atoms, 128 MB for 2,000 atoms), plus `5 x N` doubles per thread on the heap for the output reduction buffers (~21 KB/thread at 538 atoms). The inner loop runs over all third atoms `kat = 1, nat` instead of skipping pairs beyond the cutoff, which vectorizes well in registers but does extra work on very large, sparse systems.

**Tests:** `meson test --suite xtb` passes in release and debug builds (38 passed, 1 expected failure), and `ctest -R 'xtb/*'` passes in a CMake debug build with floating-point traps (44/44).

Timings: AMD EPYC 7B13, gfortran 15.3, OpenBLAS 0.3.34, Meson release build, ALPB water (except the 538-atom complex, gas phase), pinned to one 8-core CCD on an otherwise idle machine, builds interleaved; median of 7 runs for the cyclosporin gradients and 5 for the remdesivir optimizations and the 538-atom complex.

This is one of three independent PRs (dispersion gradient, integrals, SCC) that touch separate files. Together they halve the 1-thread remdesivir optimization and cyclosporin gradient times.

Developed with AI coding assistants.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68fe777a0241`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.