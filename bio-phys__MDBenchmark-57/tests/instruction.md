# Issue

**Title:** Refactor common MD engine functions

## Description

Changes made in this pull request:
- Consolidate `write_bench` function from `mdengines.gromacs.write_bench` and `mdengines.namd.write_bench` into `mdengines.utils.write_benchmark`.
- Add unit tests to `mdengines.utils.write_benchmark`. We now also check wheter all variables in the generated `bench.job` were replaced correctly.
- Consolidate `cleanup_before_restart` for both NAMD and GROMACS.
- Consolidate `parse_ns_day`, `parse_ncores` and `analyze_run` for both NAMD and GROMACS.

PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - ~[ ] Issue raised/referenced?~

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `313352605004`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.