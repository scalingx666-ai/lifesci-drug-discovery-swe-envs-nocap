# Issue

**Title:** Fix 2 retry pipeline bugs on GPU

## Description

The retry path in src/skala/pyscf/retry.py contained two gpu4pyscf incompatibilities that together caused single-point calculations to fail on GPU but succeed on CPU for systems whose first SCF call did not converge.

1. SCFState.post_cycle_callback asserted isinstance(envs["norm_ddm"], (float, int)) but gpu4pyscf stores norm_ddm as a 0-d cupy.ndarray, so the assertion fires on the first GPU SCF cycle. This PR always converts to float to make gpu4pyscf and pyscf compatible.

2. increment_level_shift did `if level_shift > 0`. CPU pyscf defaults SCF.level_shift to 0, gpu4pyscf defaults it to None, so the comparison raises TypeError on the GPU retry path. This PR treats None and 0 identically as "no level shift yet" and start from level_shift_init.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `6223b92f79f8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.