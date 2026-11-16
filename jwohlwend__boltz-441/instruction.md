# Issue

**Title:** Improve `TrainingDataset __getitem__` performance

## Description

While exploring the Boltz codebase, I spotted a few low-hanging fruits to optimize the `__getitem__` method in `TrainingDataset`. I used `cProfile` to compare timings before and after, and as profiling data I used samples from the [preprocessed RCSB dataset](https://github.com/jwohlwend/boltz/blob/main/docs/training.md#download-the-pre-processed-data). During the profiling, I set the seed to 42 for both sampling and cropping (the non-deterministic steps), and I ran the profiling on the same data points (N=10).

Key changes:
	•	In `tokenize()`, replaced the recursive `astuple()` with a faster, direct conversion (`token_astuple`).
	•	Batched the `atom_to_token` update instead of assigning one key at a time.
	•	In `construct_paired_msa`, replaced lists with deque to get O(1) `popleft()` calls.
	•	In `prepare_msa_arrays`, built the Numba-typed dictionary directly, removing the intermediate Python one.

Results (per `__getitem__` call), averaged on 10 samples:
	•	Total: 0.59s (down from 1.06s)
	•	Tokenization: 0.07s (down from 0.46s)
	•	Featurization: 0.24s (down from 0.33s)

Changes were applied to both v1 and v2, though profiling was only done on v1 as v2 doesn’t currently run for me (which seems expected per README).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `70d50faae777`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.