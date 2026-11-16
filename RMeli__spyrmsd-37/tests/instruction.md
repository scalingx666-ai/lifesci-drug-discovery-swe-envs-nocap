# Issue

**Title:** Additional tests on randomly selected systems

## Description

## Description

Add additional tests, selected randomly from the PDBbind refined set. Results are compared with [OpenBabel](http://openbabel.org/wiki/Main_Page). 

All SDF files and OpenBabel results are downloaded from [RMeli/PDBBind-docking](https://github.com/RMeli/PDBbind-docking). The additional tests can be run with the `--large` option.

The `--runslow` option for benchmark tests has been changed to `--benchmark`.

## Checklist

- [x] Tests
- [x] Documentation

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `587f5772a90b`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.