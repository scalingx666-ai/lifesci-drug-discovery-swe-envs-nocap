# Issue

**Title:** Use `importlib.metadata`

## Description

Replaces `importlib_metadata` with `importlib.metadata` in the benchmark package. The latter is supposed to be used for versions above Python 3.8 and avoids a `mypy` issue that showed up in #205.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5ff629be5a65`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.