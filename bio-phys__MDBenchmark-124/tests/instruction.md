# Issue

**Title:** Make generate work with relative file paths

## Description

.

Changes made in this pull request:
- Fixed a bug, where running `mdbenchmark generate --name ../md.tpr` would copy the file `md.tpr` to the wrong destination folder.
- Fixed a bug where specifying `mdbenchmark generate --name md.namd` would not parse the file name correctly.

PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [x] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `742c5c464cd2`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.