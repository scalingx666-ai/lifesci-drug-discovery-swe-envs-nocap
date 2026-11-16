# Issue

**Title:** ci: skip OCSR tests so CI does not download DECIMER models

## Description

## Problem

The Python test job on #831 failed even though all tests passed:

- **66 minutes of setup.** `test session starts` printed at 11:34, but pytest started at 10:28. The tests themselves took 4 minutes.
- **Crash at exit.** After `1735 passed, 3 skipped`, Python crashed with a segmentation fault (exit code 139).

## Cause

`app/modules/decimer.py` imports DECIMER and decimer_segmentation at module level. On import, they download several GB of models from Zenodo and load TensorFlow. Every test file imports `app.main`, and `app.main` imports the OCSR router.

## Fix

- CI sets `INCLUDE_OCSR=false`. The switch already exists in `app/main.py`, and with it the OCSR router is left out of the app.
- New `tests/conftest.py`: when `INCLUDE_OCSR` is false, it skips `test_decimer.py`, `test_ocsr.py` and `test_deeplearningtools.py`.
- CI no longer installs `decimer` and `decimer-segmentation`.
- Local runs are unchanged. By default, OCSR and its tests still run.

## Expected effect

- The test job should drop to about 15–20 minutes.
- TensorFlow is never imported in CI, which should also stop the exit crash. This PR's CI run will confirm it.

## Note

Codecov will show lower project coverage, because the OCSR modules are no longer exercised in CI.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `b4dc8c548272`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.