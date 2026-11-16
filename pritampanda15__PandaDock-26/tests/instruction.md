# Issue

**Title:** Document the CPU vs GPU redocking benchmark, caveat included

## Description

Measured on 14 complexes, one per protein family of the 815-complex benchmark, docked from scratch on both devices with identical inputs and seeds. Adds --device and --n-chains to redock_benchmark.py so the comparison is reproducible and so the full set can be run on CUDA.

The result worth reporting is not the total but the scaling. GPU wall time is nearly flat in ligand flexibility -- 16 s to 84 s across the whole set -- while CPU time spans 15 s to 2522 s, because CPU cost scales with exhaustiveness times torsion count and the batched search absorbs that into one wider batch. Speedup runs 1.1x at 0-2 torsions to 26.1x at 21+, and the worst complex in the set, a 32-torsion ligand, went from 42 minutes to 84 seconds. Overall 11.1x, or ~129 h against ~11.6 h extrapolated to all 815.

The README states plainly that this is not a like-for-like comparison, because it is not. The GPU ran a fixed 256 chains x 8 hops while the CPU used its auto exhaustiveness, so part of the speedup is simply searching less -- and the accuracy shows it: top-1 within 2 A falls from 42.9% to 28.6%, best-of-9 from 57.1% to 35.7%. A citable number needs the GPU budget raised until the success rate matches and only then compared on time. Given how flat GPU time is, that may cost little, but it has to be measured.

As a check on the harness rather than on either device, the CPU best-of-9 figure here (57.1%) agrees with the 57.0% reported for the full set in the manuscript.

Raw per-complex results are not committed: .gitignore excludes benchmarking/**/*.csv, and that policy is left alone.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c54d00a8244d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.