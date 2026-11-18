# Issue

**Title:** fix(UnitCell): constructing infinite cell from zero lengths

## Description

I noticed that infinite cells are not persistent when writing and then reading .gro files.
This is because we [write zeros](https://github.com/chemfiles/chemfiles/blob/master/src/formats/GRO.cpp#L227) for infinite cells. But when reading we find 3 values and construct a unit cell from those values. The result is an orthorhombic cell with lengths zero. This breaks distances and other stuff.

I guess it would be good to also handle setter functions similar (as described in #69) in the long run.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c509f3ac9621`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.