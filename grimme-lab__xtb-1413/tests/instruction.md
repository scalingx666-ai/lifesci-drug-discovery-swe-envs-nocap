# Issue

**Title:** Improve CMake reuse of vendored subprojects

## Description

- Fix CMake target reuse so that subprojects already introduced by nested FetchContent/subproject builds are not added again, avoiding duplicate targets such as `test-drive`, `test-drive-lib`, and related test executables.
- Add Meson dist symlinks, so the CMake build can reuse the dependency sources already included in the dist tarball instead of downloading another copy online.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `2b5cd4829290`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.