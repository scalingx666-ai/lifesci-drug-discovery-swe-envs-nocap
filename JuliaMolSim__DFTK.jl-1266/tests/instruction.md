# Issue

**Title:** Optimize Ω+K a little

## Description

- Use unnormalized FFTs in `compute_δρ` and `apply_K`.
- Reduce allocations in `Ω`.

This seems to give a ~20% improvement. Not great, not terrible. In principle we can get a factor of 2 by not duplicating the FFTs, but this would make the code a lot messier and increase the memory usage. :/ (we compute `ifft(ψ)` and `ifft(δψ)` twice, and we also compute `fft(δV ψ)` and `fft(V δψ)` separately which could be summed up before the FFT).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `96e554221d03`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.