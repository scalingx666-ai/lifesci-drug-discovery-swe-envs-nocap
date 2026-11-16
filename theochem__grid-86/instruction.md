# Issue

**Title:** Improve docstring of grid base class and improve get_subgrid

## Description

A bunch of unit tests were added to make sure get_subgrid works as expected in various scenarios.

I've also remove self._size and the way it was used in MolGrid. Constructors of subclasses should not use or change attributes defined by the parent class.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `689bd7e67a17`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.