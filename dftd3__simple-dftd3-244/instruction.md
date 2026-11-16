# Issue

**Title:** Accelerate Ewald calculation

## Description

- Prepare kernel constants once, skip unused C6 and ATM work, remove unused buffers, and move repeated calculations out of inner loops.
- Support radix-2/3 FFT meshes to avoid excessive padding, and reuse kernel values for opposite wave vectors while handling Nyquist planes correctly.
- Combine symmetric pole contributions and streamline mesh initialization and contraction.

For the supplied [576-atom cell](https://github.com/user-attachments/files/33771946/1.xyz.txt) with `OMP_NUM_THREADS=24 ./s-dftd3 1.xyz --zero pbe --grad --ewald`, wall time has decreased from `96.536 s` to `2.726 s`.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6a0bb18ed2b6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.