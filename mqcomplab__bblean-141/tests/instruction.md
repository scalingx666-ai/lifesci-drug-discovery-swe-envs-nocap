# Issue

**Title:** BitBirch best practices

## Description

- Added functionalities to _py_similarity.py to do stratified samping. 
- Changed complementary similarity for a more efficient version (proven by KZ)
- Modified the recluster_inplace method, now it's able to do multiple rounds and change the threshold
- Corrected a problem in the dump_assignments method. Comparing an array with a bool is deprecated. 
- Created a jupyter nb showing the best practices to determine the threshold and how to refine the cluster to recover singletons and incorporate them into clusters.


TODO: Test command line use of recluster_inplace, improve the stratified sampling function

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `08c9bd0deaa3`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.