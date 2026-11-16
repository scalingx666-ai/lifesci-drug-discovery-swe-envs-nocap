# Issue

**Title:** NAF DF tensor reduction for MP2

## Description

## Description
Example for constructing a NAF DF tensor in the AO basis and use it for MP2.

## What are your new additions? Please provide a brief list.
* **New Features**
  - [x] NAF DF tensor reduction: M. Kállay, J. Chem. Phys. 2014, 141, 244113. http://aip.scitation.org/doi/10.1063/1.4905005

* **Notes**
I haven't had the chance to check against the MRCC implementation. Algorithmic details
might be slightly different, too.

## Status
- [x] ready for review

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `31d405e351ed`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.