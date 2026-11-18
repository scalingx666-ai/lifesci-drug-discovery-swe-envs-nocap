# Issue

**Title:** Fix stale GPU MPI rank/size during MFCC's MPI_COMM_SELF swap

## Description

## Summary
- `mfcc_fragment_scf` temporarily swaps the Fortran-level MPI communicator to `MPI_COMM_SELF`/rank=0/size=1 so each rank can independently solve its own standalone MFCC fragment, but never updated the separate C-side `gpu->mpi_comm_rank`/`gpu->mpi_comm_size` fields read by `mgpu_eri_greedy_distribute()`/`mgpu_oei_greedy_distribute()`.
- Under the CUDA+MPI build, each rank kept computing only its original ~1/N share of the fragment's two-electron integrals with no real reduction to recombine the rest, corrupting the MFCC initial-guess densities fed into the main DnC-SCF — causing DnC+MFCC to oscillate for 100+ cycles instead of converging in ~8.
- Adds `mgpu_get_rank_size_`/`mgpu_set_rank_size_` getter/setter functions (mirrored in both `src/gpu/cuda/mgpu.h` and `src/gpu/hip/mgpu.h`, since `MPIV_GPU` is defined for both GPU platforms) and saves/overrides(`0,1`)/restores the C-side rank/size around the `MPI_COMM_SELF` window in `src/dnc/mfcc_fragment_scf.f90`, mirroring the existing Fortran-level save/restore.

## Test plan
- [x] CUDA+MPI DnC+MFCC on Trp-cage now converges in 8 cycles at `-7344.023670747` Ha, matching serial/mpi/cuda flavors to 7+ decimals (previously oscillated for 100+ cycles).
- [x] Full local regression suite (`runtest --<flavor> --full`) on HPC: serial, mpi, cuda, cudampi all pass clean (0 failures).
- [x] GitHub Actions Serial and MPI workflows on this branch: both pass.
- [ ] GitHub Actions CUDA workflows: queued but no self-hosted GPU runner currently registered on the fork, so they can't execute there; CUDA/CUDA+MPI correctness was instead validated via the local HPC regression suite above.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `72a8e5f15f65`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.