# Issue

**Title:** adds the routine used in Hydrogens to update double bond stereo elements after atom/bond removal to AtomContainer atom removal

## Description

In reference to 

The changes are applied to data AtomContainer and silent AtomContainer. Tests are also added.

@johnmay, please advise whether this is what you proposed in the issue linked above.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b2996d233d21`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.