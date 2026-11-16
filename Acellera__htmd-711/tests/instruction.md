# Issue

**Title:** Refactoring of Molecule file reading

## Description

As promised here comes the big PR.
So as per the discussion we had on multi-mol MOL2 file reader. 
We needed the readers to be able to return multiple molecules. In readers.py I have the Topology and Trajectory classes which I only use temporarily to collect all the data in the file because appending to lists is faster than appending to numpy arrays which is what Molecule uses. 

So then I needed a way to convert a Topology+Trajectory to a Molecule. Until now this was done inside the Molecule class. This however creates the problem that if you read a file with multiple molecules you need to instantiate multiple Molecule objects which could not be done in `Molecule.read`. So I moved the Molecule creation part out of Molecule now to a MolFactory class which creates Molecule objects. Then the readers can use that to return one or more Molecules. This allows us now to read multiple molecules from a single file by using directly the file reader.

Hence the `Molecule.read` now gets from the readers one or more `Molecule` objects which it then tries to merge into itself.

And to answer the probably inevitable question, the `MolFactory` is not meant to be instantiated. It's a static class of the "factory/builder" pattern https://en.wikipedia.org/wiki/Builder_pattern. It probably doesn't follow the patterns to the T but I hope you don't mind. Yes, I could have made it a function instead of a class but I thought it nicer to group the functions together in that way. Your taste may vary.

If this takes too long to merge it will probably become a mess to merge later since it changes some core stuff in Molecule so please @j3mdamas review the soonest possible.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `911ed6c8fbcb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.