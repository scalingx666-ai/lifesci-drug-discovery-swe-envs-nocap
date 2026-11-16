# Issue

**Title:** Update CLI options

## Description

.

Changes made in this pull request:
- Added `--number-cores` to `mdbenchmark analyze`.
- Renamed `--module-name` to `--module` in `mdbenchmark plot`.
- Renamed `--host-name` to `--host` in `mdbenchmark plot`.
- Added `--template` and `-t` to `mdbenchmark plot`. It's a synonym for `mdbenchmark `-host`
- Added `-c/-nc` and `-g/-ng` short options for `--cpu/--no-cpu` and `--gpu/--no-gpu`, respectively.
- Renamed `--output-type` to `--output-format`.
- Renamed `-t` as short option to `-f`.

PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [x] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `71c76ba9959f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.