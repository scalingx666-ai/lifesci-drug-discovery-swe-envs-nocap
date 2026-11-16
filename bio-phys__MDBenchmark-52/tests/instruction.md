# Issue

**Title:** Update plotting interface

## Description

Updated plotting interface. `mdbenchmark analyze --plot` is not deprecated. Use `mdbenchmark plot` instead.

The new workflow for plotting data is as follows:

1) Use `mdbenchmark analyze` to generate a CSV output file.
2) Use `mdbenchmark plot --csv name_of_generated_file.csv` to plot the data.

Consult `mdbenchmark <command> --help` for options to filter your data accordingly.


PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [x] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2af31992f002`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.