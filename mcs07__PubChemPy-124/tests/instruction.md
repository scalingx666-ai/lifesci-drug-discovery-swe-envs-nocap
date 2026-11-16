# Issue

**Title:** Better error handling

## Description

- Add support for HTTP code 503 ServerBusy
- Refactor the functionality that raises the correct subclass from the HTTPError
- Add pytest-rerunfailures for TimeoutError and ServerBusyError. Configured with `--reruns 3 --reruns-delay 5 --only-rerun TimeoutError --only-rerun ServerBusyError`
- Fix a test that was using a deprecated API which was causing a warning

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d81a44240c2d`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.