# Issue

**Title:** Reduce linear-algebra work in the SCC loop

## Description

`TEigenSolver` now inverts the Cholesky factor of S once at setup (`mctc_potrf` + `mctc_trtri`), in both single and double precision. Each SCC iteration reduces H to standard form with trmm/gemm, solves it with `lapack_sytrd` + `lapack_stedc`, and back-transforms only the requested eigenvector columns (`fact_solve_subspace` / `fact_backtransform`). `scc` back-transforms the occupied orbitals during the iterations and the rest once after convergence, so H still holds all eigenvectors on return, and removes the unused `X` workspace array. `dmat` uses `mctc_syrk` for the uniformly occupied orbitals plus a small `mctc_gemm` for fractionally occupied ones.

| Case | main | this PR | Time saved |
| :--- | ---: | ---: | ---: |
| CREST conformer search, rivaroxaban (47 atoms), `-T 4` | 267.2 s | 250.9 s | 6% |
| Geometry optimization, remdesivir (77 atoms), 1 thread | 7.33 s | 7.55 s | none (within noise) |
| Geometry optimization, remdesivir (77 atoms), 4 threads | 4.57 s | 4.16 s | 9% |
| Gradient, cyclosporin A (196 atoms), 1 thread | 1.11 s | 0.94 s | 15% |
| Gradient, cyclosporin A (196 atoms), 4 threads | 0.60 s | 0.53 s | 11% |
| Gradient, LNCI16 2xHB238 complex (538 atoms), 4 threads | 13.28 s | 10.39 s | 22% |

The gain grows with system size, since it removes O(N^3) work per SCC iteration. Results agree with main to round-off, not bitwise: orbitals with occupation below 1e-16 are left out of the density during the iterations, and `syrk` sums in a different order. The density matrix is unchanged, but eigenvectors of degenerate orbitals can come out rotated, so molden and localized-orbital output may differ. Cyclosporin A energies match main to all 12 printed decimals and gradients agree to 5e-15 Eh/bohr; the remdesivir optimizations take the same 50 steps to the same energy (to 5e-11 Eh); on the 538-atom complex the gradient agrees to 7e-15 Eh/bohr. CREST finds the same conformers within its run-to-run variation (with `-T 4` it is not bit-reproducible).

The `USE_CUSOLVER` build now also allocates the CPU workspaces, since `scc` uses these routines; it could not be tested because that build does not compile on main (, which merges cleanly with this PR).

**Tests:** `meson test --suite xtb` passes in release and debug builds (38 passed, 1 expected failure), and `ctest -R 'xtb/*'` passes in a CMake debug build with floating-point traps (44/44).

Timings: AMD EPYC 7B13, gfortran 15.3, OpenBLAS 0.3.34, Meson release build, ALPB water (except the 538-atom complex, gas phase), pinned to one 8-core CCD on an otherwise idle machine, builds interleaved; median of 7 runs for the gradients, 5 for the optimizations, 3 for the 538-atom complex and 4 for CREST (CREST 2.12, `--gfn2 --alpb water --opt normal --mquick`; standalone table measured on 1aa6181 before moving `property.F90` to #1465).

This is one of three independent PRs (dispersion gradient, integrals, SCC) that touch separate files. Together they cut the CREST example by 43% and the 1-thread optimization by 49%.

Developed with AI coding assistants.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68fe777a0241`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.