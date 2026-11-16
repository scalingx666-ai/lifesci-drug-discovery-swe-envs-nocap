# Issue

**Title:** [pre-commit.ci] pre-commit autoupdate

## Description

<!--pre-commit.ci start-->
updates:
- [github.com/asottile/setup-cfg-fmt: v2.8.0 → v3.1.0](https://github.com/asottile/setup-cfg-fmt/compare/v2.8.0...v3.1.0)
- [github.com/asottile/pyupgrade: v3.20.0 → v3.21.0](https://github.com/asottile/pyupgrade/compare/v3.20.0...v3.21.0)
- [github.com/pycqa/isort: 6.0.1 → 7.0.0](https://github.com/pycqa/isort/compare/6.0.1...7.0.0)
- https://github.com/psf/black → https://github.com/psf/black-pre-commit-mirror
<!--pre-commit.ci end-->

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `a291dacbc9c9`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.