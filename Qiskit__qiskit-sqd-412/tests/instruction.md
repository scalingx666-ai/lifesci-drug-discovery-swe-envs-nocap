# Issue

**Title:** Fix static TLS headroom and bump tox min_version to 4.21.2 (backport #411)

## Description

### Summary

This PR addresses two CI environment issues affecting Linux builds:

1. **Static TLS headroom on Linux**:
   - Moves the `GLIBC_TUNABLES = glibc.rtld.optional_static_tls=4096` workaround (from #397) to the base `[testenv]` section in `tox.ini`.
   - This ensures all Linux test environments (including the unit test `py` environment, `coverage`, and `docs`) inherit adequate static TLS headroom, resolving `cannot allocate memory in static TLS block` errors during test collection with qiskit 2.6.0 and pyscf (as recently seen in scheduled runs on `main`).

2. **Bump tox minimum version to 4.21.2**:
   - Bumps `min_version` in `tox.ini` and `pyproject.toml` to 4.21.2.
   - Starting in tox 4.4.4+, tox passes `$HOME` by default on POSIX. In minimum version tests (`test_minimum_versions.yml`), tox was previously pinned to 4.4.3, which stripped `$HOME`. With GitHub Actions recently migrating `ubuntu-latest` to Ubuntu 26.04 (bringing in Open MPI 5), `sbd-eigensolver` builds from source were failing because Open MPI's `opal_init()` requires the user home directory.<hr>This is an automatic backport of pull request #411 done by [Mergify](https://mergify.com).

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `d4933cf657d8`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.