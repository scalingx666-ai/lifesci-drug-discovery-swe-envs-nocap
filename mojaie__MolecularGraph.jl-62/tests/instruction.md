# Issue

**Title:** add support for V3000 format and rxn files

## Description

I've added preliminary support for extended mol-file format (V3000) and reading of reaction files into a tuple of GraphMol Vectors (reactants and products) (see my issues #60, #61)
 
One could think of adding a reaction type later, but for my use case the current changes are already very helpful. I've also not yet added radical information.

One technical remark.
I've modified `sdftomol()` to automatically detect the extended format and to read reaction files. As a consequence `parse(SDFile, ...)` results in either a GraphMol object or in a tuple of vectors of `Graphmol`. From a type stabilty view point this is not so nice. One could also think about splitting the two parsers. But I thought, it's nice to have just the one interface.

Happy to hear what you think.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `e5196c1a021d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.