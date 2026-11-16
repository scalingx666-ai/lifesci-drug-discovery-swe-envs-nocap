# Issue

**Title:** Final CLI Improvements

## Description

The PR makes the following updates:

1. The `--random` flag is set by default now in the example command, so the example command now indeed generates random samples unless `predefined` is requested, and an example file actually exists.
2. The `--as-table` flag for the `run` command has a shorter `-t` flag now.
3. `catalog` command accepts any extension and supports both tab separated files and comma separated files, however when the file extension is not `.tsv`, it serializes the file as a CSV by default.
4. The `example` command logs to the user if it is unable to find an example file for the model and that it is generating random samples.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `203879efe278`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.