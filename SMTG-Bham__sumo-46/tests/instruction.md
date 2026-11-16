# Issue

**Title:** Enable repeat labels on band structure, made unique internally with trailing @

## Description

Another "secret labels" feature to aid with use of custom k-point paths. High-symmetry points are handled in Pymatgen and Sumo as a dictionary of labels and positions. This means that it is prohibited to re-use the same label for a different k-point, even if that position is actually symmetry-equivalent or a periodic image in reciprocal space.

There are arguments for and against using such band structures, but here we provide a workaround for those who wish to re-use labels for non-equivalent points. By appending an '@' symbol to the label in
KPOINTS or syml.ext (i.e. 'X' becomes 'X@'), a new special point is identified which will also display as 'X' in the plotted band structure. What if you need another one? Just add more @ signs, the code uses regular expressions to look for a block of @ signs at the end of the label.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `3b169b9a7b3d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.