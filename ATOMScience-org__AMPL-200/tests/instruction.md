# Issue

**Title:** Replace dc.data.DiskDataset with NumpyDataset and otherwise reduce creation of temp files

## Description

This branch replaces all uses of the deepchem DiskDataset class with NumpyDataset. There was never a good reason to use DiskDataset because the sizes of datasets we train models on were never big enough to benefit from sharding. In addition, the way we used DiskDataset (by calling the static from_numpy method) automatically put everything in one shard, so we've been dealing with the extra file I/O overhead without any gain. Using NumpyDataset should make model training and inference faster, and eliminate the temporary files that were generated every time the GMD loop made predictions from an AMPL model.

This branch also includes a fix to model_version_utils.get_ampl_version_from_model to read the model_metadata.json from a tarfile stream, without having to untar the model tarball first. This removes another source of excess temp files that was causing problems for the GMD loop.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `dc7dbd735ebd`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.