# Issue

**Title:** Make rustworkx the default backend in pip

## Description

## Description

Close 

* Make `rustworkx` the default backend when installing with `pip`
  * The same change will be reflected in the condo-forge recipe
* Change the order of precedence for the default backend: `networkx` is the very last resort

## Checklist

- [x] Tests
- [x] Documentation
- [x] Changelog

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d58d18e16fe6`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.