# Issue

**Title:** Speed up overlap, dipole and quadrupole integrals and their gradients

## Description

`get_multiints` and `get_grad_multiint` now build 1D Obara-Saika tables once per primitive pair and form all 10 multipole components and their derivatives from them, instead of calling `multipole_3d` / `multipole_grad_3d` for every Cartesian component pair. Shell pairs whose most diffuse primitives already fall below the integral cutoff are skipped, using the same estimate as the existing primitive screening, so skipped pairs contribute exactly zero. Both routines now zero only the active `(1:naoj, 1:naoi)` block of their output buffers, which is all the callers read. `dtrf2` is skipped when neither shell is a d shell. In `build_SDQH0` and `build_dSDQH0`, the lattice-translation loop and distance cutoff move outside the shell loops. `main_property` only recomputes S and the multipole integrals when a printout needs them. The OpenMP loops are unchanged.

| Case | main | this PR | Time saved |
| :--- | ---: | ---: | ---: |
| CREST conformer search, rivaroxaban (47 atoms), `-T 4` | 267.2 s | 178.7 s | 33% |
| Geometry optimization, remdesivir (77 atoms), 1 thread | 7.33 s | 4.40 s | 40% |
| Geometry optimization, remdesivir (77 atoms), 4 threads | 4.57 s | 3.51 s | 23% |
| Gradient, cyclosporin A (196 atoms), 1 thread | 1.11 s | 0.81 s | 27% |
| Gradient, cyclosporin A (196 atoms), 4 threads | 0.60 s | 0.51 s | 14% |
| Gradient, LNCI16 2xHB238 complex (538 atoms), 4 threads | 13.28 s | 12.18 s | 8% |

The new 1D tables match main to round-off, not bitwise; the shell-pair screening is exact. `H0_noovlp` no longer gets the `hav*shpoly` term for screened pairs or for images beyond the distance cutoff, but its only consumer (`build_dSDQH0_noreset`) multiplies it by S, which is zero at those pairs, so gradients are unchanged. Cyclosporin A energies match main to all 12 printed decimals and gradients agree to 3e-15 Eh/bohr; the remdesivir optimizations take the same 50 steps to the same energy (to 2e-11 Eh); on the 538-atom complex the gradient agrees to 8e-15 Eh/bohr. CREST finds the same conformers; with `-T 4` it is not bit-reproducible, so main and this PR each sometimes find one extra conformer 0.3 kcal/mol lower.

**Tests:** `meson test --suite xtb` passes in release and debug builds (38 passed, 1 expected failure), and `ctest -R 'xtb/*'` passes in a CMake debug build with floating-point traps (44/44).

Timings: AMD EPYC 7B13, gfortran 15.3, OpenBLAS 0.3.34, Meson release build, ALPB water (except the 538-atom complex, gas phase), pinned to one 8-core CCD on an otherwise idle machine, builds interleaved; median of 7 runs for the gradients, 5 for the optimizations, 3 for the 538-atom complex and 4 for CREST (CREST 2.12, `--gfn2 --alpb water --opt normal --mquick`; standalone table measured on 31ec813 before moving `property.F90` here from #1466).

This is one of three independent PRs (dispersion gradient, integrals, SCC) that touch separate files. Together they cut the CREST example by 43% and the 1-thread optimization by 49%.

Developed with AI coding assistants.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `68fe777a0241`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.