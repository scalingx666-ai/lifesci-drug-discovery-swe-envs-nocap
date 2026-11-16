# Issue

**Title:** Add --cpu flag to generate

## Description

.

Changes made in this pull request:
- `mdbenchmark generate` now accepts `--cpu` / `--no-cpu`, as well as a `--gpu` / `--no-gpu` options. If given both `--cpu` and `--gpu`, it will generate both benchmarks at once. The default is `--cpu` and `--no-gpu`.

PR Checklist
------------
 - [x] Added changelog fragment in  `./changelog/` ([more information](https://github.com/bio-phys/MDBenchmark/blob/master/DEVELOPER.rst#using-towncrier))?
 - [x] Issue raised/referenced?

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `95fb6fbca8a7`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.