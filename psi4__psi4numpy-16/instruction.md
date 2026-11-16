# Issue

**Title:** EOM-CCSD

## Description

Adds modules for computing Hbar elements and doing a simple EOMCCSD computation. 


This can be very slow, but if you have access to Numpy 1.12 adding the kwarg optimize=True in the contractions for evaluating the sigma vectors will save a lot of time. 

The Davidson solver is not very robust and for some some cases where the number of roots requested involves the first one or two roots of a triplet set it will fail or converge to nonsensical complex roots. 

Any suggestions on how to improve the efficiency or the stability of the Davidson routine would be appreciated

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `f7e10050d298`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.