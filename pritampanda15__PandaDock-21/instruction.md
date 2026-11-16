# Issue

**Title:** Stream SAIR CIFs from S3

## Description

Each CIF is read exactly once, to build its graph; training thereafter reads
only the cache. Syncing the full set would cost about 432 GB of local disk
(457 KB x 923,653) for data touched once, so cif_root now accepts an s3:// prefix
and files are streamed.

The boto3 client is created once per process. Constructing one per file dominates
runtime at this scale, and the connection pool is sized for parallel
preprocessing workers.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b61959086614`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.