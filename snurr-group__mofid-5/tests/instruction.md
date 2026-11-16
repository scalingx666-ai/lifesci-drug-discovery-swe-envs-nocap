# Issue

**Title:** Use single node topology by default

## Description

This PR continues the work from #1 and applies the "single node" deconstruction algorithm by default.  If a MOF has multiple topological representations, e.g. from the "all node" algorithm or the user, they can be specified using a comma-separated list within MOFid, with the base topology listed first.

The SBU assignment now includes carboxylate carbons and the functional group as part of the SBU, regardless of coordination mode (a single oxygen end-on, chelated to two metals, etc.).  These changes lay the groundwork for general deconstruction of rod-like topologies as well, hopefully in a future commit.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `55cd618e921f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.