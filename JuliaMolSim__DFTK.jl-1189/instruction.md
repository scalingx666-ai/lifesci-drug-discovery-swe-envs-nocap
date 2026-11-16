# Issue

**Title:** Ensure contiguous occupations

## Description

This PR adds checks to ensure that occupations are contiguous. In various places in the code, it is simply assumed that occupied and empty orbitals are clearly separated (e.g. [here](https://github.com/JuliaMolSim/DFTK.jl/blob/e2672b6d4f89cb6be307fec7d5048cf9663762d0/src/scf/nbands_algorithm.jl#L88-L91) or [here](https://github.com/JuliaMolSim/DFTK.jl/blob/e2672b6d4f89cb6be307fec7d5048cf9663762d0/src/orbitals.jl#L8-L10)). This is currently not a safe assumption, as it is not enforced.

This PR adds a check on eigenvalues monotonocity when computing the occupations. Additionally, a helper function providing masks in the form of ranges (useful for taking views into GPU arrays) was added. Finally, the creation of supercells now enforces consistent reordering of the eigenvalues and wave-functions.

Note: range masks are not used in `densities.jl`, as the `compute_density()` function is sometime hijacked in other contexts, where the assumption on occupations does not hold (e.g. [here](https://github.com/JuliaMolSim/DFTK.jl/blob/e2672b6d4f89cb6be307fec7d5048cf9663762d0/src/postprocess/dos.jl#L61-L64))

This PR is a necessary fix for #1187 tests to pass.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e2672b6d4f89`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.