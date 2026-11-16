# Issue

**Title:** GPU stage 1: batched grid scoring, verified against the CPU implement…

## Description

…ation

First step of the GPU search: port AffinityGrids.score_and_gradient to torch so that thousands of poses are scored in one call, and prove it agrees with the CPU path before anything is built on top of it.

The CPU search is what the manuscript validated on 814 complexes. This code has no independent claim to correctness, so the tests compare it against the CPU implementation rather than against hand-written expectations, and additionally check the analytic gradient against finite differences so that two implementations wrong in the same way would still be caught.

Device handling is explicit rather than discovered at runtime. MPS has no float64 at all, so dtype_for_device pins float64 on CPU/CUDA and float32 on MPS in one place, and the parity tolerances follow from it.

One deliberate numerical difference, now documented and pinned by a test. The production maps are float32, and the CPU x-derivative starts from `c100 - c000`, a subtraction of two raw float32 values that loses about seven digits to cancellation before promotion. The y and z derivatives subtract already-promoted intermediates and are bit-identical. Uploading the maps as float64 makes this implementation the more accurate of the two, so agreement on the x-gradient is ~1e-8 relative rather than round-off; energies are unaffected because they never difference two corners. The test records that this is the only disagreement, so a later change cannot quietly reintroduce a real indexing bug under cover of an already-loose tolerance.

Also removes monte_carlo_gpu.py, genetic_algorithm_gpu.py and enhanced_hierarchical_gpu.py. They were imported nowhere, and as algorithms/__init__ already noted, their chromosome encoded only translation and orientation, so they could not vary ligand conformation. They are a misleading starting point for this work, not a foundation for it.

Measured on this machine, 4,096 poses of a 17-heavy-atom ligand against a 66^3 x 4 grid: 34k poses/s for the current one-at-a-time NumPy path, 770k batched on CPU, 1.10M on MPS. Most of that is batching rather than the device, which is worth knowing before any speedup is claimed for CUDA.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f2c3b3cd338e`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.