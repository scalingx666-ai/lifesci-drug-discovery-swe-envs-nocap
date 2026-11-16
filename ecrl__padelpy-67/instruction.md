# Issue

**Title:** Harden supply-chain security controls

## Description

## Summary
- Add a CI `audit` job (`pip-audit --strict` on the default install and `[dev]` extras) and list `pip-audit` under the `[dev]` optional dependency set.
- Pin `pypa/gh-action-pypi-publish` to commit SHA `ba38be9…` (v1.14.1) and expand `SECURITY.md` with private GitHub advisory reporting, a threat model, and a SHA-256 inventory of vendored PaDEL artifacts (with an integrity unit test).

## Test plan
- [x] CI `audit` job passes on this PR
- [x] CI lint/test/docs jobs remain green
- [x] Confirm private vulnerability reporting stays enabled under repo Security settings
- [x] Optionally verify locally: `shasum -a 256 -c docs/security/vendored-artifacts.sha256` and `pip install -e ".[dev]" && pip-audit --strict`

Made with [Cursor](https://cursor.com)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `c9d66968182d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.