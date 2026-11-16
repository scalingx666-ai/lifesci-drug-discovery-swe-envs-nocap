# Issue

**Title:** Fixes in msa processing script

## Description

Fixes in the `scripts/process/msa.py` script to make it functional,
- Changed `data = args.msadir.rglob("*.a3m*")` to ` data = list(args.msadir.rglob("*.a3m*"))`. As `args.msadir.rglob("*.a3m*")` returns a generator and `len()` of generator isn't valid.
- `shared_data` is created in the `process_msa` call, therefore removed it from the `process` function.
- `max_seqs` wasn't passed in the `process_msa` call in both the parallel and non-parallel cases. `outdir` wasn't passed in the non-parallel case. 

Minor comment: In case `len(data) < num_processes`, the `parallel` variable can be set to False as it can lead to empty lists when creating chunks. Let me know if you want me to update the PR with that edge case.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3f4e834aa007`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.