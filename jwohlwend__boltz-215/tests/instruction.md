# Issue

**Title:** feat: allow cache directory to be set via BOLTZ_CACHE environment variable

## Description

Adds support for setting the cache directory via the `BOLTZ_CACHE` environment variable
Changes made:

- The cache defaults to `BOLTZ_CACHE` value if set, otherwise falls back to ~/.boltz 
- Validation to ensure path resolves to absolute path.
- If BOLTZ_CACHE is set and --cache is also used, the setting in --cache option takes priority.

Why needed?
This is to provide flexibility in a cluster that sets up an environment for a user avoiding individual download / copies of the cache checkpoint data where they wont necessarily know of a pre-existing shared location

Tested manually with and without `BOTLZ_CACHE` set and with `--cache`  confirmed no errors,
I'm not sure if the validation is necessary (I guess it's best to always check)  I couldn't find a path that didn't resolve

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `5f515995cfca`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.