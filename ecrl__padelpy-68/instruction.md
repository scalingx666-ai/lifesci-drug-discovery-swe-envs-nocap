# Issue

**Title:** Harden CI and repository infrastructure for future development

## Description

## Summary
- Expand CI with concurrency/pip caching, a `pre-commit` job, Windows/macOS smoke tests, CodeQL, and a non-blocking Codecov upload (token deferred).
- Gate PyPI publish on a full test job; add root `NOTICE` for vendored PaDEL/CDK; link live Read the Docs from the README.

## Test plan
- [x] CI `lint`, `pre-commit`, `audit`, `docs`, and `test (3.12)` pass (required checks for `master`)
- [x] `smoke (windows-latest)` and `smoke (macos-latest)` pass
- [x] CodeQL workflow runs successfully
- [x] Codecov step does not fail the job without `CODECOV_TOKEN`
- [x] Confirm `pypi` environment still has required reviewer + wait timer (repo settings; already configured)

Made with [Cursor](https://cursor.com)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `95407ab21dcb`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.