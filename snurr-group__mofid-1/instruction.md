# Issue

**Title:** More deconstruction algorithms

## Description

This PR implements additional algorithms to deconstruct a MOF into its building blocks for topological assignment.  Notably, it implements the "single node" and "all node" algorithms recommended by an [ongoing IUPAC project](https://pubs.acs.org/doi/10.1021/acs.cgd.8b00126).  These algorithms will supersede the original MOFidDeconstructor for topology detection, though the MOF chemistry should still be described by the simple organic/inorganic split from the original algorithm.

Additional representations of the MOF are written to subdirectories of the designated output directory, e.g. `Output/SingleNode/` and `Output/AllNode/`.

In a future branch, I will incorporate these analyses as part of the high-throughput screening workflow.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `48f28c7ea6af`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.