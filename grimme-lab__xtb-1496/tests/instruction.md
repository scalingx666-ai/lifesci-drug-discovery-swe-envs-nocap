# Issue

**Title:** Update static release packaging

## Description

This updates the release packaging to produce clean static binaries across Linux, macOS, and Windows with tblite, ddX, and CPCM-X enabled.

The release archives now use a curated layout containing only the xTB/cpx executables, `xtb.h`, `libxtb.a`, `libcpx.a`, runtime parameter files, manpages, and the required license notices.

The previous extensive release-validation logic was removed again after verifying the artifacts across all supported platforms, keeping the production CI focused and minimal.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `9e3ccc0dc38f`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.