# Issue

**Title:** Make SmallRingDescriptor, WienerNumbersDescriptor, and ALogPDescriptor parallelisable

## Description

In the three descriptor classes, instance variables relating to the current calculation, i.e. the given molecule, were turned into local method variables and are now passed between internal private methods as parameters, so that the classes are parallelisable.

We are doing descriptor calculations for batches of molecules and tried different ways of doing that in parallel for speed-up. This way, we realised that only these three descriptors were not parallelisable. 

@egonw, since it was only three in the end, I didn't report them to you directly but instead went on to simply fix them immediately.

I also "linted" the classes a bit here and there and fixed some smaller Sonar complaints.

What do you think?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a48fb6537746`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.