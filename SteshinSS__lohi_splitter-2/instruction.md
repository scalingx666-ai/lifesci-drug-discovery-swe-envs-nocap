# Issue

**Title:** Memory-efficient Lo split algorithm

## Description

I was using the Lo splitter for a QSAR modeling project with a larger dataset (600k+ molecules) and ran into issues with memory usage. After digging into the code, I found a few areas that could be optimized. Here’s what I changed:

- Moved the fingerprint and similarity calculations outside the clustering loop.
- Stored only the similarities above a threshold using a CSR (Compressed Sparse Row) matrix to save memory.
- Reduced the dataset size step by step during clustering.
- Replaced some loops with NumPy vectorized operations.

The original code would have needed around 1.37 TiB of RAM just to store the similarity matrix (using 32-bit floats). With these changes, I was able to run everything on regular hardware without problems.

**Performance improvements**
When running the example notebook, this implementation reduced execution time while still returning the same clusters for the input dataset.
- Train/test split: 2m50s -> 56s
- K-fold CV: 8m25s -> 2m46s

Let me know if anything needs tweaking or if you'd like further changes. Feel free to merge if you find it useful!

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5c0fafb709c6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.