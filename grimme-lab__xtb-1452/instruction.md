# Issue

**Title:** CI: Add source-dist workflow

## Description

Add a self-contained source distribution to the xtb CI.
- Build `xtb-*.tar.xz` with `meson dist --include-subprojects` for offline installation.
- Upload the source archive as a release artifact.
- Rename the existing bleed Linux binary archive to `xtb-bleed-linux-x86_64.tar.xz`.
- Reserve `xtb-bleed.tar.xz` for the Meson source distribution.

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `fa035bce99a5`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.