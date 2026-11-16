# Issue

**Title:** perf(release): use zstd compression for the RPM bundle

## Description

Tauri's RPM bundler defaults to gzip-6; the ~240MB bundled backend made the rpm step the Linux build's long pole (~1.5h vs ~15s for .deb). Switch to zstd level 3 (faster, comparable ratio). Applies next release.

🤖 Generated with [Claude Code](https://claude.com/claude-code)

## Task

Modify the repository so that the issue described above is resolved. The repository is checked out at base commit `8453ba56af6a`. Edit files in place; the verifier captures your changes via `git diff` and scores them against an oracle patch using SWE-RL-style diff-similarity reward.